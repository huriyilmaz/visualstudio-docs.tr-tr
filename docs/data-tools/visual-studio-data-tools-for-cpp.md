---
title: C++ için veri araçları
description: C++ Visual Studio veri araçlarını keşfedin. Bağlan C++ uygulamasından ODBC ve SQL yerel istemci aracılığıyla localDB'ye bağlanır.
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
ms.openlocfilehash: 8376adeeedbb4bbdae10d147573799813da95bec
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631082"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ için Visual Studio veri araçları

Yerel C++, veri kaynaklarına erişirken genellikle en hızlı performansı sağlar. Ancak, C++ uygulamaları için veri Visual Studio .NET uygulamaları için olduğu kadar zengin değildir. Örneğin Veri Kaynakları **penceresi,** veri kaynaklarını bir C++ tasarım yüzeyine sürükleyip bırakmak için kullanılamaz. Nesne ilişkisel bir katmana ihtiyacınız varsa kendi ürünlerinizi yazmanız veya üçüncü taraf bir ürün kullanmanız gerekir. Aynı durum veri bağlama işlevselliği için de geçerli olsa da, Microsoft Foundation Sınıf kitaplığını kullanan uygulamalar bellekte veri depolamak ve kullanıcıya görüntülemek için belgeler ve görünümlerle birlikte bazı veritabanı sınıflarını kullanabilir. Daha fazla bilgi için [bkz. Visual C++.](/cpp/data/data-access-in-cpp)

Yerel C++ SQL veritabanına bağlanmak için, yerel C++ uygulamaları OLE DB'ye dahil olan ODBC ve OLE DB ADO sağlayıcısını Windows. Bunlar, bu arabirimleri destekleyen herhangi bir veritabanına bağlanabilirsiniz. ODBC sürücüsü standarttır. OLE DB uyumluluk için sağlanmıştır. Bu veri teknolojileri hakkında daha fazla bilgi için [bkz. Windows Veri Erişimi Bileşenleri.](/previous-versions/windows/desktop/ms692897(v=vs.85))

2005 ve sonraki bir SQL Server özel işlevden yararlanmak için, yerel [SQL Server kullanın.](/sql/relational-databases/native-client/sql-server-native-client) Yerel istemci, tek bir yerel SQL Server bağlantı kitaplığında (DLL) SQL Server OLE DB ODBC sürücüsünü ve SQL Server OLE DB sağlayıcısını da içerir. Bu uygulamalar, yerel kod API'lerini (ODBC, OLE DB ve ADO) kullanarak uygulamaları Microsoft SQL Server. SQL Server Native Client ile SQL Server Veri Araçları. Programlama kılavuzu buradadır: [SQL Server istemci programlama.](/sql/relational-databases/native-client/sql-server-native-client-programming)

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>ODBC ve C++ uygulamasından SQL Native Client localDB'ye bağlanmak için

1. Yükleme SQL Server Veri Araçları.

2. Bağlanmak için örnek bir SQL veritabanına ihtiyacınız varsa, Northwind veritabanını indirin ve yeni bir konuma sıkıştırmayı açın.

3. Sıkıştırması SQL Server Management Studio *Northwind.mdf* dosyasını localDB'ye eklemek için dosya adını kullanın. Bağlantı SQL Server Management Studio,(localdb)\MSSQLLocalDB'ye bağlanin.

   ![SSMS bağlantı iletişim kutusu](../data-tools/media/raddata-ssms-connect-dialog.png)

   Ardından sol bölmedeki localdb düğümüne sağ tıklayın ve Ekle'yi **seçin.**

   ![SSMS veritabanı ekleme](../data-tools/media/raddata-ssms-attach-database.png)

4. ODBC Windows SDK Örneği'ni indirin ve sıkıştırmayı yeni bir konuma açın. Bu örnek, bir veritabanına bağlanmak ve sorgu ve komutlar oluşturmak için kullanılan temel ODBC komutlarını gösterir. Bu işlevler hakkında daha fazla bilgi için [bkz. Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Çözümü (C++ klasöründedir) ilk kez yükleyemediniz, Visual Studio çözümün geçerli sürümüne yükseltmeyi Visual Studio. **Evet**'e tıklayın.

5. Yerel istemciyi kullanmak için üst bilgi dosyası *ve* *lib dosyası* gerekir. Bu dosyalar sql.h içinde tanımlanan ODBC işlevlerinin SQL Server özel işlevler ve tanımlar içerir. Bu **Project**  >    >  **VC++ Dizinleri'ne** aşağıdaki ekleme dizinini ekleyin:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Ve bu kitaplık dizini:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. *Odbcsql.cpp'ye bu satırları ekleyin.* Bu #define, ilgisiz OLE DB tanımların derlenemlerini önler.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Örneğin aslında yerel istemci işlevlerinden herhangi birini kullanmaz, bu nedenle derlemesi ve çalıştırması için yukarıdaki adımlar gerekli değildir. Ancak proje artık bu işlevi kullanmak üzere yapılandırılmıştır. Daha fazla bilgi için [bkz. SQL Server Native Client programlama.](/sql/relational-databases/native-client/sql-server-native-client)

7. ODBC alt sisteminde hangi sürücünün kullan kullanır olduğunu belirtin. Örnek, DRIVER bağlantı dizesi özniteliğini komut satırı bağımsız değişkeni olarak iletir. Özellikler **Project**  >    >  **Ayıklama'ya** şu komut bağımsız değişkenlerini ekleyin:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Sürücüden veritabanı girmenizi İstenen bir iletişim kutusu görüyor olun. girin `(localdb)\MSSQLLocalDB` ve Güvenilen Bağlantı **Kullan'a gözdin.** **Tamam**'a basın. Başarılı bir bağlantı olduğunu belirten iletilere sahip bir konsol görüyorsanız. Ayrıca, bir SQL deyimini yazarak da SQL gerekir. Aşağıdaki ekranda örnek bir sorgu ve sonuçlar gösterilir:

   ![ODBC örnek sorgu çıkışı](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
