---
title: Estado del puerto de la regla de FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a33286ffb678bf37cf684bb603d81ec8091e7405
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568823"
---
# <a name="fxcop-rule-port-status"></a>Estado del puerto de la regla de FxCop

Si anteriormente usó el análisis de código estático en Visual Studio, es posible que se pregunte qué reglas están disponibles en la implementación actual como [analizadores de FxCop](install-fxcop-analyzers.md). En esta página se enumeran las reglas que se portan, así como las que no se han migrado y si hay planes para trasladarlas.

## <a name="ported-rules"></a>Reglas migradas

La [Página de documentación autogenerada](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) del repositorio Roslyn-analizadores tiene la lista más actualizada de reglas que se han trasladado a los analizadores de FxCop. Esa página también tiene información adicional, por ejemplo, si la regla está habilitada de forma predeterminada y si tiene una *corrección de código*asociada. (Las[correcciones de código](../ide/quick-actions.md) son correcciones con un solo clic disponibles en el menú del icono de bombilla de Visual Studio).

A partir de la fecha de esta página, la lista de reglas de FxCop que se han trasladado a los [analizadores de FxCop](install-fxcop-analyzers.md) incluye:

Identificador de la regla | Title
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | No declarar miembros estáticos en tipos genéricos
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Los tipos que poseen campos descartables deben ser descartables
[CA1003](ca1003-use-generic-event-handler-instances.md) | Utilizar instancias genéricas de controlador de eventos
[CA1008](ca1008-enums-should-have-zero-value.md) | Las enumeraciones deben tener un valor igual a cero
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Las colecciones deben implementar la interfaz genérica
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Los tipos abstractos no deberían tener constructores
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Marcar ensamblados con CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Marcar ensamblados con versión de ensamblado
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Marcar ensamblados con ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Marcar atributos con AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Definir descriptores de acceso para los argumentos de atributo
[CA1024](ca1024-use-properties-where-appropriate.md) | Utilizar las propiedades donde corresponda
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Marcar enumeraciones con FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | El almacenamiento de enumeración debe ser Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Utilizar eventos cuando sea apropiado
[CA1031](ca1031-do-not-catch-general-exception-types.md) | No capturar los tipos de excepción general
[CA1032](ca1032-implement-standard-exception-constructors.md) | Implementar constructores de excepción estándar
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Los tipos secundarios deben poder llamar a los métodos de interfaz
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Los tipos anidados no deben ser visibles
[CA1036](ca1036-override-methods-on-comparable-types.md) | Invalidar métodos en tipos comparables
[CA1040](ca1040-avoid-empty-interfaces.md) | Evitar las interfaces vacías
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Proporcionar un mensaje ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Usar el argumento integral o de cadena para los indizadores
[CA1044](ca1044-properties-should-not-be-write-only.md) | Las propiedades no deben ser de solo escritura
[CA1050](ca1050-declare-types-in-namespaces.md) | Declarar tipos en espacios de nombres
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | No declarar campos de instancia visibles
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Los tipos de titulares estáticos deben ser estáticos o NotInheritable
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Los tipos de titulares estáticos no deben tener constructores (CA1053 es parte de [CA1052](ca1052-static-holder-types-should-be-sealed.md) para los analizadores de FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Los parámetros de URI no deben ser cadenas
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Los valores devueltos de URI no deben ser cadenas
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Las propiedades URI no deben ser cadenas
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Los tipos no deben ampliar ciertos tipos base
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Move pinvokes a la clase de métodos nativos
[CA1061](ca1061-do-not-hide-base-class-methods.md) | No ocultar métodos de clase base
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Validar argumentos de métodos públicos
[CA1063](ca1063-implement-idisposable-correctly.md) | Implementar IDisposable correctamente
[CA1064](ca1064-exceptions-should-be-public.md) | Las excepciones deben ser públicas
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | No producir excepciones en ubicaciones inesperadas
CA1066 | El tipo {0} debe implementar el > de \<T IEquatable porque invalida Equals.
CA1067 | Invalide Object. Equals (Object) al implementar IEquatable \<T >
[CA1068](ca1068.md) | Los parámetros CancellationToken deben aparecer en último lugar
CA1200 | Evitar el uso de etiquetas cref con un prefijo
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | No pasar literales como parámetros localizados
[CA1304](ca1304-specify-cultureinfo.md) | Especificar CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Especificar IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Especificar StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normalizar cadenas en mayúsculas
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Usar comparación de cadenas ordinales
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Los elementos P/Invoke no deben estar visibles
[CA1501](ca1501-avoid-excessive-inheritance.md) | Evitar una herencia excesiva
[CA1502](ca1502-avoid-excessive-complexity.md) | Evitar una complejidad excesiva
[CA1505](ca1505-avoid-unmaintainable-code.md) | Evitar código que no se puede mantener
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Evitar el acoplamiento excesivo de clases
[CA1507](ca1507.md) | Usar nombre para expresar nombres de símbolos
CA1508 | Evitar código condicional inactivo
CA1509 | Entrada no válida en el archivo de especificación de regla de métricas de código
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Los identificadores no deben contener caracteres de subrayado
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Los identificadores deben tener un sufijo correcto
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Los identificadores no deben tener un sufijo incorrecto
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | No utilizar prefijos en valores de enumeración con el nombre del tipo
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Las enumeraciones Flags deben tener nombres en plural
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Los identificadores deben tener el prefijo correcto
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Los identificadores no deben coincidir con palabras clave
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Solo las enumeraciones FlagsAttribute deben tener nombres en plural
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | El identificador contiene el nombre de tipo
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Los nombres de propiedades no deben coincidir con los métodos get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Los nombres de tipo no deben coincidir con los espacios de nombres
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Los nombres de parámetro deben coincidir con la declaración base
[CA1801](ca1801.md) | Revisar parámetros sin utilizar
[CA1802](ca1802.md) | Usar literales cuando corresponda
[CA1806](ca1806.md) | No omitir resultados del método
[CA1810](ca1810.md) | Inicializar campos estáticos de tipo de referencia insertados
[CA1812](ca1812.md) | Evitar las clases internas sin instancia
[CA1813](ca1813.md) | Evitar los atributos no sellados
[CA1814](ca1814.md) | Preferir matrices escalonadas antes que multidimensionales
[CA1815](ca1815.md) | Invalidar Equals y el operador Equals en los tipos de valores
[CA1816](ca1816.md) | Los métodos Dispose deben llamar a SuppressFinalize
[CA1819](ca1819.md) | Las propiedades no deben devolver matrices
[CA1820](ca1820.md) | Comprobar si las cadenas están vacías mediante la longitud de cadena
[CA1821](ca1821.md) | Quitar finalizadores vacíos
[CA1822](ca1822.md) | Marcar miembros como estáticos
[CA1823](ca1823.md) | Evitar los campos privados sin utilizar
[CA1824](ca1824.md) | Marcar los ensamblados con NeutralResourcesLanguageAttribute
CA1825 | Evite las asignaciones de matrices de longitud cero.
CA1826 | No use métodos enumerables en colecciones indizables. En su lugar, use la colección directamente
[CA2000](ca2000.md) | Desechar objetos antes de perder el ámbito
[CA2002](ca2002.md) | No bloquear objetos con identidad débil
[CA2007](ca2007.md) | Considere la posibilidad de llamar a ConfigureAwait en la tarea esperada
CA2008 | No crear tareas sin pasar un TaskScheduler
CA2009 | No llamar a ToImmutableCollection en un valor de ImmutableCollection
CA2010 | Usar siempre el valor devuelto por los métodos marcados con PreserveSigAttribute
[CA2100](ca2100.md) | Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad
[CA2101](ca2101.md) | Especificar serialización en argumentos de cadena P/Invoke
[CA2119](ca2119.md) | Sellar los métodos que satisfacen las interfaces privadas
[CA2153](ca2153.md) | No capturar excepciones de estado dañadas
[CA2200](ca2200.md) | Vuelva a iniciar para conservar los detalles de la pila.
[CA2201](ca2201.md) | No provocar tipos de excepción reservados
[CA2207](ca2207.md) | Inicializar campos estáticos de tipo de valor insertados
[CA2208](ca2208.md) | Crear instancias de las excepciones del argumento correctamente
[CA2211](ca2211.md) | Los campos no constantes no deben ser visibles
[CA2213](ca2213.md) | Los campos descartables deben ser descartables
[CA2214](ca2214.md) | No llamar a métodos reemplazables en constructores
[CA2216](ca2216.md) | Los tipos descartables deben declarar el finalizador
[CA2217](ca2217.md) | No marcar enumeraciones con FlagsAttribute
[CA2218](ca2218.md) | Invalidar el método GetHashCode al invalidar el método Equals
[CA2219](ca2219.md) | No producir excepciones en cláusulas Finally
[CA2224](ca2224.md) | Invalidar Equals al sobrecargar el operador Equals
[CA2225](ca2225.md) | Las sobrecargas del operador tienen alternativas con nombre
[CA2226](ca2226.md) | Los operadores deben tener sobrecargas simétricas
[CA2227](ca2227.md) | Las propiedades de la colección deben ser de solo lectura
[CA2229](ca2229.md) | Implementar constructores de serialización
[CA2231](ca2231.md) | Sobrecargar el operador de igualdad al reemplazar el tipo de valor es igual a
[CA2234](ca2234.md) | Pasar objetos URI del sistema en lugar de cadenas
[CA2235](ca2235.md) | Marcar todos los campos no serializables
[CA2237](ca2237.md) | Marcar los tipos ISerializable con serializable
[CA2241](ca2241.md) | Proporcionar argumentos correctos a los métodos de formato
[CA2242](ca2242.md) | Comprobar NaN correctamente
[CA2243](ca2243.md) | Los literales de cadena de atributo se deben analizar correctamente
CA2244 | No duplicar inicializaciones de elementos indizados
[CA2300](ca2300.md) | No usar el deserializador no seguro BinaryFormatter
[CA2301](ca2301.md) | No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder
[CA2302](ca2302.md) | Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize
[CA2305](ca2305.md) | No usar el deserializador no seguro LosFormatter
[CA2310](ca2310.md) | No usar el deserializador no seguro NetDataContractSerializer
[CA2311](ca2311.md) | No deserializar sin establecer primero NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar
[CA2315](ca2315.md) | No usar el deserializador no seguro ObjectStateFormatter
[CA2321](ca2321.md) | No deserializar con JavaScriptSerializer mediante SimpleTypeResolver
[CA2322](ca2322.md) | Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar
[CA3001](ca3001.md) | Revisión de código en busca de vulnerabilidades de inyección de SQL
[CA3002](ca3002.md) | Revisión de código en busca de vulnerabilidades de XSS
[CA3003](ca3003.md) | Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos
[CA3004](ca3004.md) | Revisión de código en busca de vulnerabilidades de divulgación de información
[CA3005](ca3005.md) | Revisión de código en busca de vulnerabilidades de inyección de LDAP
[CA3006](ca3006.md) | Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos
[CA3007](ca3007.md) | Revisión de código en busca de vulnerabilidades de redireccionamiento abierto
[CA3008](ca3008.md) | Revisión de código en busca de vulnerabilidades de inyección de XPath
[CA3009](ca3009.md) | Revisión de código en busca de vulnerabilidades de inyección de XML
[CA3010](ca3010.md) | Revisión de código en busca de vulnerabilidades de inyección de XAML
[CA3011](ca3011.md) | Revisión de código en busca de vulnerabilidades de inyección de DLL
[CA3012](ca3012.md) | Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares
CA3061 | No agregar esquema por dirección URL
[CA3075](ca3075.md) | Procesamiento de DTD no seguro en XML
[CA3076](ca3076.md) | Procesamiento de script XSLT no seguro.
[CA3077](ca3077.md) | Procesamiento inseguro en el diseño de API, XmlDocument y XmlTextReader
[CA3147](ca3147.md) | Marcar los controladores de verbos con validar token antifalsificación
[CA5350](ca5350.md) | No usar algoritmos criptográficos no seguros
[CA5351](ca5351.md) | No usar algoritmos criptográficos rotos
CA5358 | No usar modos de cifrado no seguros
CA5359 | No deshabilitar la validación de certificados
CA5360 | No llamar a métodos peligrosos en la deserialización
CA5361 | No deshabilite el uso de SChannel de cifrado seguro
CA5362 | No hacer referencia a sí mismo en una clase serializable
CA5363 | No deshabilitar la validación de solicitudes
CA5364 | No usar protocolos de seguridad en desuso
CA5365 | No deshabilitar la comprobación de encabezados HTTP
CA5366 | Usar XmlReader para leer el XML de DataSet
CA5367 | No serializar tipos con campos de puntero
CA5368 | Establecer ViewStateUserKey para las clases derivadas de Page
CA5369 | Usar XmlReader para deserializar
CA5370 | Usar XmlReader para validar el lector
CA5371 | Usar XmlReader para leer el esquema
CA5372 | Usar XmlReader para XPathDocument
CA5373 | No usar la función de derivación de clave obsoleta
CA5374 | No usar XslTransform
CA5375 | No usar firma de acceso compartido de cuenta
CA5376 | Uso de SharedAccessProtocol HttpsOnly
CA5377 | Usar la Directiva de acceso de nivel de contenedor
CA5378 | No deshabilitar ServicePointManagerSecurityProtocols
CA5379 | No usar algoritmo de función de derivación de clave débil
CA9999 | Versión de analizador no coincidente

## <a name="unported-rules"></a>Reglas no trasladadas

El conjunto de reglas que no se han migrado a los [analizadores de FxCop](install-fxcop-analyzers.md) consta de reglas que todavía no se [pueden portar](#rules-that-may-be-ported)y que están desusadas y que [no se portan](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Reglas que se pueden portar

Las siguientes reglas de análisis heredado de FxCop todavía no se han implementado como analizadores, pero todavía pueden ser. Esto puede deberse a una razón técnica de bloqueo o simplemente a que la regla tiene una prioridad más baja. Para obtener más información acerca del estado de portabilidad de cada regla, haga clic en el vínculo de la columna **problema de seguimiento** .

Identificador de la regla | Problema de seguimiento
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Reglas en desuso

Las siguientes reglas de análisis heredado de FxCop están desusadas y no se implementarán como analizadores. Para obtener más información, puede buscar por el identificador de regla (por ejemplo, **CA1009**) en la [Página de problemas de github Roslyn-analizadores](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([justificación](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122:](ca5122.md)

## <a name="see-also"></a>Vea también

- [Reglas de Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
