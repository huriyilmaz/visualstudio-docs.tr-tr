---
title: 'CA2100: güvenlik açıkları için SQL sorgularını Inceleyin | Microsoft Docs'
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
ms.openlocfilehash: 797c071cdc74c36afeece304bfa4c708d7bf7147
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521218"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL sorgularını güvenlik açıkları için inceleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Yöntemi, <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> yöntemine dize bağımsız değişkeninden oluşturulan bir dize kullanarak özelliği ayarlar.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, dize değişkeninin kullanıcı girişi içerdiğini varsayar. Kullanıcı girişi ile oluşturulan SQL komut dizesi, SQL enjeksiyon saldırılarına karşı savunmasız durumdadır. Bir SQL ekleme saldırısında, kötü niyetli bir Kullanıcı, bir sorgunun tasarımını değiştiren ve temel alınan veritabanına yetkisiz erişim elde eden bir giriş sağlar. Tipik teknikler, SQL sabit dize sınırlayıcısı olan tek tırnak işareti veya kesme işareti ekleme işlemini içerir; bir SQL yorumunu belirten iki tire; ve yeni bir komutun izlediği noktalı virgül. Kullanıcı girişi sorgunun bir parçası olmalıdır, saldırı riskini azaltmak için, verimlilik sırasıyla listelenen aşağıdakilerden birini kullanın.

- Saklı yordam kullanın.

- Parametreli bir komut dizesi kullanın.

- Komut dizesini oluşturmadan önce hem tür hem de içerik için Kullanıcı girişini doğrulayın.

  Aşağıdaki [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] türler <xref:System.Data.IDbCommand.CommandText%2A> özelliği uygular veya bir dize bağımsız değişkeni kullanarak özelliği ayarlamış olan oluşturucular sağlar.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> ve <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> ve <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> ve <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System. Data. SqlServerCe. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) ve [System. Data. SqlServerCe. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> ve <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Bir türün ToString yöntemi açıkça veya sorgu dizesini oluşturmak için örtük olarak kullanıldığında bu kuralın ihlal edildiğini unutmayın. Bir örnek verilmiştir.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Kötü amaçlı bir Kullanıcı ToString () metodunu geçersiz kılabildiğinden kural ihlal edilir.

 Ayrıca, ToString örtük olarak kullanıldığında kural da çiğnendir.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için parametreli bir sorgu kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Komut metni herhangi bir kullanıcı girişi içermiyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı `UnsafeQuery` ve `SaferQuery` parametreli bir komut dizesi kullanarak kuralı karşılayan yöntemini ihlal eden bir yöntemi gösterir.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenliğe genel bakış](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
