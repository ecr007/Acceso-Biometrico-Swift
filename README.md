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
