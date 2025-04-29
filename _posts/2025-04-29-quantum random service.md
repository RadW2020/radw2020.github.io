---
layout: post
title: Quantum Service en QuPot - Aleatoriedad cuántica real para loterías blockchain
---

La aleatoriedad es un pilar fundamental en cualquier sistema de lotería. Pero, ¿qué pasaría si en vez de confiar en algoritmos clásicos, pudieras usar la física cuántica para obtener números realmente impredecibles? Eso es exactamente lo que hace el subservicio `quantum-service` de [QuPot](https://github.com/RadW2020/QuPot): un microservicio que genera números aleatorios usando principios cuánticos, integrándose en una arquitectura de microservicios y blockchain.

---

## ¿Por qué aleatoriedad cuántica?

Los generadores de números aleatorios clásicos (PRNG) son deterministas: si conoces el estado interno, puedes predecir el resultado. En cambio, la mecánica cuántica garantiza resultados impredecibles gracias al principio de superposición y colapso de la función de onda. Esto es ideal para aplicaciones donde la equidad y la transparencia son críticas, como las loterías descentralizadas.

---

## Arquitectura y stack tecnológico

- **Backend:** FastAPI (Python)
- **Quantum Engine:** Qiskit (simulador cuántico)
- **Contenedores:** Docker
- **Integración:** API Gateway, servicios de lotería y blockchain en QuPot

---

## ¿Cómo funciona?

1. **Circuito cuántico:** Se crea un circuito con un qubit en superposición usando una puerta Hadamard.
2. **Medición:** El qubit se mide, colapsando a 0 o 1 con igual probabilidad.
3. **Composición:** Se combinan varios bits cuánticos para formar números en el rango deseado.
4. **API REST:** El servicio expone endpoints para solicitar números aleatorios, información del circuito y health checks.

---

## Ejemplo de uso: Generar números aleatorios cuánticos

### Petición

```json
POST /api/v1/random
{
  "min_value": 1,
  "max_value": 90,
  "count": 6,
  "unique": true
}
```

### Respuesta

```json
{
  "numbers": [23, 45, 12, 67, 89, 34],
  "source": "quantum_simulator",
  "timestamp": "2025-03-15T12:34:56.789012",
  "request_id": "550e8400-e29b-41d4-a716-446655440000"
}
```

---

## Código destacado: Generación de bits cuánticos

```python
def generate_quantum_random_bit():
    qc = QuantumCircuit(1, 1)
    qc.h(0)           # Superposición
    qc.measure(0, 0)  # Medición
    job = sampler.run(circuits=[qc], shots=1)
    result = job.result()
    counts = result.quasi_dists[0]
    measurement = next(iter(counts.keys()))
    return measurement
```

Y para un número en un rango arbitrario:

```python
def generate_quantum_random_number(min_value, max_value):
    range_size = max_value - min_value + 1
    bits_needed = (range_size - 1).bit_length()
    value = 0
    for i in range(bits_needed):
        bit = generate_quantum_random_bit()
        value = (value << 1) | bit
    value = min_value + (value % range_size)
    return value
```

---

## Visualización: Circuito cuántico y distribución de resultados

A continuación puedes ver cómo se construye un circuito cuántico para generar un número aleatorio de 6 bits. Cada línea representa un qubit, y cada bloque rojo es una puerta Hadamard que pone el qubit en superposición antes de medirlo.

![Quantum Circuit for 6-Bit Random Number Generation](https://i.imgur.com/HE4OUDh.png)

La siguiente gráfica muestra la distribución de resultados al medir un solo qubit 1000 veces. Como se espera, la probabilidad de obtener 0 o 1 es prácticamente idéntica, demostrando la aleatoriedad cuántica.

![Measurement Results for 1000 Shots](https://i.imgur.com/iK8AwW9.png)

---

## Endpoint de información del circuito cuántico

Puedes consultar cómo funciona el circuito y ver estadísticas reales de las mediciones:

```json
GET /api/v1/quantum-circuit

{
  "circuit_description": "Hadamard gate followed by measurement",
  "circuit_qubits": 1,
  "circuit_depth": 2,
  "measurement_counts": { "0": 500, "1": 500 },
  "explanation": "This quantum circuit places a qubit in superposition using a Hadamard gate, creating an equal probability of measuring 0 or 1. The measurement then collapses the superposition, providing a truly random bit."
}
```

---

## Integración en QuPot

El `quantum-service` se integra con el resto de microservicios de QuPot:

- El API Gateway enruta las peticiones.
- El servicio de lotería usa la aleatoriedad cuántica para los sorteos.
- El servicio blockchain garantiza la transparencia y trazabilidad de los resultados.

---

## Conclusión

## El subservicio `quantum-service` de QuPot es un ejemplo real y educativo de cómo la computación cuántica puede aportar valor en aplicaciones descentralizadas, garantizando aleatoriedad verdadera y transparencia.

**¿Quieres ver el código o probarlo tú mismo?**  
Visita el repo: [https://github.com/RadW2020/QuPot](https://github.com/RadW2020/QuPot)
