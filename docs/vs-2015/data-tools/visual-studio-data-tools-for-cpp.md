---
title: '| İçin C++ Visual Studio veri araçları Microsoft Docs'
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621203"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ için Visual Studio veri araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerel C++ , veri kaynaklarına erişirken genellikle en hızlı performansı sağlayabilir. Ancak, Visual Studio 'daki uygulamalar C++ için veri araçları, .NET uygulamaları için olduğu kadar zengin değildir. Örneğin, veri kaynakları penceresi C++ tasarım yüzeyine veri kaynaklarını sürükleyip bırakmak için kullanılamaz. Nesne ilişkisel bir katmana ihtiyacınız varsa, kendi kendinize yazmanız veya bir üçüncü taraf ürünü kullanmanız gerekecektir.  Aynı değer, veri bağlama işlevselliği için de geçerlidir, ancak Microsoft Foundation Class kitaplığını kullanan uygulamalar, verileri bellekte depolamak ve kullanıcıya göstermek için belgeler ve görünümler ile birlikte bazı veritabanı sınıflarını kullanabilir. Daha fazla bilgi için bkz. [Visual C++ 'te veri erişimi](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Yerel C++ uygulamalar, SQL veritabanlarına bağlanmak için ODBC ve OLE DB sürücülerini ve Windows ile bırlıkte gelen ADO sağlayıcısını kullanabilir.     Bunlar, bu arabirimleri destekleyen herhangi bir veritabanına bağlanabilir. ODBC sürücüsü standarttır. OLE DB geriye dönük uyumluluk için sağlanır. Bu veri teknolojileri hakkında daha fazla bilgi için bkz. [Windows veri erişim bileşenleri](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)

 SQL Server 2005 ve sonraki sürümlerde özel işlevlerden faydalanmak için [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733)kullanın. Yerel istemci Ayrıca, tek bir yerel dinamik bağlantı kitaplığı 'nda (DLL) SQL Server ODBC sürücüsünü ve SQL Server OLE DB sağlayıcısını da içerir. Bu, Microsoft SQL Server için yerel kod API 'Leri (ODBC, OLE DB ve ADO) kullanan uygulamaları destekler.  SQL Server Native Client SQL Server Veri Araçları yüklenir. Programlama Kılavuzu şu şekildedir: [SQL Server Native Client programlama](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>ODBC aracılığıyla localDB 'ye bağlanmak ve bir C++ uygulamadan SQL Native Client için

1. SQL Server Veri Araçları 'i yükler.

2. Bağlanılacak örnek bir SQL veritabanına ihtiyacınız varsa, Northwind veritabanını indirin ve yeni bir konuma ayıklayın.

3. Sıkıştırılmış Northwind. mdf dosyasını localDB 'ye iliştirmek için SQL Server Management Studio kullanın. SQL Server Management Studio başladığında, (LocalDB) \Mssqllocaldbdizinine bağlanın.

    ![SSMS Bağlan iletişim kutusu](../data-tools/media/raddata-ssms-connect-dialog.png "radveri SSMS Connect iletişim kutusu")

    Ardından sol bölmedeki LocalDB düğümüne sağ tıklayın ve **Ekle**' yi seçin.

    ![SSMS veritabanı Ekle](../data-tools/media/raddata-ssms-attach-database.png "radveri SSMS veritabanı Ekle")

4. ODBC Windows SDK örneğini indirin ve yeni bir konuma ayıklayın. Bu örnek, bir veritabanına bağlanmak ve sorguları ve komutları vermek için kullanılan temel ODBC komutlarını gösterir. Bu işlevler hakkında daha fazla bilgi için bkz. [Microsoft açık veritabanı bağlantısı (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Çözümü C++ ilk kez yüklediğinizde, Visual Studio çözümü Visual Studio 'nun geçerli sürümüne yükseltmeyi sağlar. **Evet**'i tıklayın.

5. Yerel istemciyi kullanmak için üst bilgi dosyası ve LIB dosyasına ihtiyacınız vardır. Bu dosyalar, SQL. h içinde tanımlanan ODBC işlevlerinin ötesinde SQL Server özgü işlevler ve tanımlar içerir. **Project**  > **Özellikler**  > **VC + + dizinleri**' nde aşağıdaki içerme dizinini ekleyin:

   **\<system sürücü >: \Program FILES\MICROSOFT SQL Server\110\sdk\ınclude**     Ve bu kitaplık dizini:

   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**

6. Bu satırları odbcsql. cpp öğesine ekleyin. #Define, ilgisiz OLE DB tanımlarının derlenmelerini engeller.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Örnek aslında yerel istemci işlevlerinin hiçbirini kullanmaz, bu nedenle önceki adımların derlenmesi ve çalışması için gerekli değildir. Ancak proje artık bu işlevselliği kullanabilmeniz için yapılandırılmıştır. Daha fazla bilgi için bkz. [SQL Server Native Client programlama](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. ODBC alt sisteminde kullanılacak sürücüyü belirtin. Örnek, içindeki sürücü bağlantı dizesi özniteliğini bir komut satırı bağımsız değişkeni olarak geçirir. **Proje**  > **Özellikler**  > **hata ayıklama**' da bu komut bağımsız değişkenini ekleyin:

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. Sürücüden bir veritabanı girmenizi isteyen bir iletişim kutusu görmeniz gerekir. @No__t_0 girin ve **güvenilir bağlantıyı kullan**' ı işaretleyin. **Tamam**'a basın. Başarılı bir bağlantı olduğunu belirten iletilerle bir konsol görmeniz gerekir. Ayrıca, bir SQL ifadesine yazabileceğiniz bir komut istemi de görmeniz gerekir. Aşağıdaki ekranda örnek bir sorgu ve sonuçlar gösterilmektedir:

    ![ODBC örnek sorgu çıkışı](../data-tools/media/raddata-odbc-sample-query-output.png "radveri ODBC örnek sorgu çıkışı")

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
