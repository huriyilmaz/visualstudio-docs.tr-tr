---
title: C++ için veri araçları
description: C++ için Visual Studio veri araçlarını gezin. bir C++ uygulamasından ODBC ve SQL yerel istemci aracılığıyla localdb 'ye Bağlan.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 69c8663d7e03a3f5bedbece6d5503c72295dea5aef619e8823aa2b69d7e21e99
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121327831"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ için Visual Studio veri araçları

Yerel C++ genellikle veri kaynaklarına erişirken en hızlı performansı sağlayabilir. ancak Visual Studio içindeki C++ uygulamaları için veri araçları, .net uygulamaları için olduğu kadar zengin değildir. Örneğin, **veri kaynakları** penceresi bir C++ tasarım yüzeyine veri kaynaklarını sürükleyip bırakmak için kullanılamaz. Nesne ilişkisel bir katmana ihtiyacınız varsa, kendi kendinize yazmanız veya bir üçüncü taraf ürünü kullanmanız gerekecektir. Aynı değer, veri bağlama işlevselliği için de geçerlidir, ancak Microsoft Foundation Class kitaplığını kullanan uygulamalar, verileri bellekte depolamak ve kullanıcıya göstermek için belgeler ve görünümler ile birlikte bazı veritabanı sınıflarını kullanabilir. Daha fazla bilgi için bkz. [Visual C++ veri erişimi](/cpp/data/data-access-in-cpp).

yerel C++ uygulamaları SQL veritabanlarına bağlanmak için ODBC ve OLE DB sürücülerini ve Windows kapsamındaki ADO sağlayıcısını kullanabilir. Bunlar, bu arabirimleri destekleyen herhangi bir veritabanına bağlanabilir. ODBC sürücüsü standarttır. OLE DB geriye dönük uyumluluk için sağlanır. bu veri teknolojileri hakkında daha fazla bilgi için bkz. [Windows data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

SQL Server 2005 ve sonraki sürümlerde özel işlevlerden faydalanmak için, [SQL Server yerel istemcisini](/sql/relational-databases/native-client/sql-server-native-client)kullanın. yerel istemci ayrıca, tek bir yerel dinamik bağlantı kitaplığı 'nda (DLL) SQL Server ODBC sürücüsünü ve SQL Server OLE DB sağlayıcısını da içerir. Bu, Microsoft SQL Server için yerel kod API 'Leri (ODBC, OLE DB ve ADO) kullanan uygulamaları destekler. SQL Server Native Client SQL Server Veri Araçları yüklenir. programlama kılavuzu şu şekildedir: [yerel istemci programlama SQL Server](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>ODBC aracılığıyla localdb 'ye bağlanmak ve bir C++ uygulamasından SQL Native Client için

1. SQL Server Veri Araçları 'i yükler.

2. bağlanmak için bir örnek SQL veritabanına ihtiyacınız varsa, Northwind veritabanını indirin ve yeni bir konuma ayıklayın.

3. sıkıştırılmış *Northwind. mdf* dosyasını localdb 'ye iliştirmek için SQL Server Management Studio kullanın. SQL Server Management Studio başladığında, (localdb) \mssqllocaldbdizinine bağlanın.

   ![SSMS Bağlan iletişim kutusu](../data-tools/media/raddata-ssms-connect-dialog.png)

   Ardından sol bölmedeki LocalDB düğümüne sağ tıklayın ve **Ekle**' yi seçin.

   ![SSMS veritabanı Ekle](../data-tools/media/raddata-ssms-attach-database.png)

4. ODBC Windows SDK örneğini indirin ve yeni bir konuma ayıklayın. Bu örnek, bir veritabanına bağlanmak ve sorguları ve komutları vermek için kullanılan temel ODBC komutlarını gösterir. Bu işlevler hakkında daha fazla bilgi için bkz. [Microsoft açık veritabanı bağlantısı (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). çözümü ilk yüklediğinizde (C++ klasöründe ise), Visual Studio çözümü güncel Visual Studio sürümüne yükseltmeyi sağlar. **Evet**'e tıklayın.

5. Yerel istemciyi kullanmak için *üst bilgi* dosyası ve *LIB* dosyasına ihtiyacınız vardır. bu dosyalar, SQL. h içinde tanımlanan ODBC işlevlerinin ötesinde SQL Server özgü işlevler ve tanımlar içerir. **Project**  >  **özellikleri**  >  **VC + + dizinlerinde** aşağıdaki içerme dizinini ekleyin:

   **% ProgramFiles% \ Microsoft SQL Server \110\sdk\include**

   Ve bu kitaplık dizini:

   **% ProgramFiles% \ Microsoft SQL Server \110\sdk\lib**

6. Bu satırları *odbcsql. cpp* öğesine ekleyin. #Define, ilgisiz OLE DB tanımlarının derlenmelerini engeller.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Örnek aslında yerel istemci işlevlerinin hiçbirini kullanmaz, bu nedenle önceki adımların derlenmesi ve çalışması için gerekli değildir. Ancak proje artık bu işlevselliği kullanabilmeniz için yapılandırılmıştır. daha fazla bilgi için bkz. [SQL Server Native Client programlama](/sql/relational-databases/native-client/sql-server-native-client).

7. ODBC alt sisteminde kullanılacak sürücüyü belirtin. Örnek, içindeki sürücü bağlantı dizesi özniteliğini bir komut satırı bağımsız değişkeni olarak geçirir. **Project**  >  **özellikler**  >  **hata ayıklaması** bölümünde şu komut bağımsız değişkenini ekleyin:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Sürücüden bir veritabanı girmenizi isteyen bir iletişim kutusu görmeniz gerekir. Yazın `(localdb)\MSSQLLocalDB` ve **güvenilir bağlantıyı kullan**' ı işaretleyin. **Tamam**'a basın. Başarılı bir bağlantı olduğunu belirten iletilerle bir konsol görmeniz gerekir. ayrıca, bir SQL ifadeye girebileceğiniz bir komut istemi görmeniz gerekir. Aşağıdaki ekranda örnek bir sorgu ve sonuçlar gösterilmektedir:

   ![ODBC örnek sorgu çıkışı](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
