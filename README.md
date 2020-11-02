# Face-ID-Touch-ID-Swift

```swift

// Se importa la clase
import LocalAuthentication

// Se crean dos variables

// Esta clase se utiliza para evaluar politicas
var context = LAContext()

var error: NSError?

// canEvaluatePolicy: Evalúa si la autenticación puede continuar para una política determinada.

if context.canEvaluatePolicy(LAPolicy.deviceOwnerAuthenticationsWithBiometrics, error: &error) {

	if context.biometryType == .faceID{
		// Estan activos los datos faciales
	}
	else if context.biometryType == .touchID{
		// Estan activos los datos dactilares
	}
	else{
		// No hay metodos biometricos disponibles
	}
}

// evaluatePolicy: Evalua una politica especificada
// Se utiliza para ejecutar una accion determinada

context.evaluatePolicy(LAPolicy.deviceOwnerAuthenticationsWithBiometrics,LocalizedReason: "Biometrics Authentications!"){
	(success, error) in

	if success {
		Dispatch.queue.asyc{
			// Goo To Controller
		}
	}
	else{
		print("Error: \(error)")
	}
}

// Importante se debe agregar el permiso al info.plist

Key: Privacy - Face ID Usage Description
Value: "String donde se solicita acceso"
```

ERRORES

```
context.evaluatePolicy(policy!, localizedReason: reasonString, reply: { (successAuth, error) in
            DispatchQueue.main.async {
             
                if successAuth
                {
                    Success(true  , nil)
                }
                else
                {
                    guard let error = error else {
                         Success(false  , "UnknownError")
                        return
                    }
                    switch (error)
                    {
                    case LAError.authenticationFailed:
                            Success(false  , error.localizedDescription)
                        break
                    case LAError.userCancel:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.userFallback:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.systemCancel:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.passcodeNotSet:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.touchIDNotAvailable:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.touchIDNotEnrolled:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.touchIDLockout:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.appCancel:
                        Success(false  , error.localizedDescription)
                        break
                    case LAError.invalidContext:
                        Success(false  , error.localizedDescription)
                        break
                    default:
                        break
                    }
                    return
              }
            }
        })
    }
  ```
