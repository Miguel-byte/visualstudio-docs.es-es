---
title: 'CA2100: revisar las consultas SQL en busca de vulnerabilidades de seguridad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e7258ec98937e7ea84773e788234e5a34772e9d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652194"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Revisar las consultas SQL en busca de vulnerabilidades de seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|Identificador de comprobación|CA2100|
|Categoría|Microsoft.Security|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método establece la propiedad <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> mediante el uso de una cadena que se genera a partir de un argumento de cadena para el método.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla supone que el argumento de cadena contiene datos proporcionados por el usuario. Una cadena de comandos de SQL compilada a partir de datos proporcionados por el usuario es vulnerable a ataques de inserción de SQL. En un ataque por inyección de SQL, un usuario malintencionado proporciona datos que alteran el diseño de una consulta en un intento de dañar u obtener acceso no autorizado a la base de datos subyacente. Entre las técnicas típicas se incluye la inserción de una comilla simple o un apóstrofo, que es el delimitador de cadena literal de SQL. dos guiones, lo que significa un comentario SQL; y un punto y coma, que indica que sigue un nuevo comando. Si los datos proporcionados por el usuario deben formar parte de la consulta, use uno de los siguientes, enumerados en orden de efectividad, para reducir el riesgo de ataque.

- Usar un procedimiento almacenado.

- Use una cadena de comandos parametrizada.

- Valide la entrada del usuario para el tipo y el contenido antes de generar la cadena de comando.

  Los siguientes tipos de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] implementan la propiedad <xref:System.Data.IDbCommand.CommandText%2A> o proporcionan constructores que establecen la propiedad mediante un argumento de cadena.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> y <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> y <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> y <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System. Data. SqlServerCe. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) y [System. Data. SqlServerCe. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> y <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Tenga en cuenta que esta regla se infringe cuando el método ToString de un tipo se usa explícita o implícitamente para construir la cadena de consulta. A continuación se muestra un ejemplo.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 La regla se infringe porque un usuario malintencionado puede invalidar el método ToString ().

 La regla también se infringe cuando se utiliza ToString implícitamente.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, use una consulta con parámetros.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el texto del comando no contiene ninguna entrada de usuario.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método, `UnsafeQuery`, que infringe la regla y un método, `SaferQuery`, que cumple la regla mediante una cadena de comandos con parámetros.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Vea también
 [Información general sobre seguridad](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
