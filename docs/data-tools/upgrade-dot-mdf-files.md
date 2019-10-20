---
title: .mdf dosyalarını yükseltme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e0196c582fbe673d73c7aeb89280d05e11a071a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639571"
---
# <a name="upgrade-mdf-files"></a>.mdf dosyalarını yükseltme

Bu konu, Visual Studio 'nun daha yeni bir sürümünü yükledikten sonra bir veritabanı dosyasını ( *. mdf*) yükseltme seçeneklerini açıklamaktadır. Aşağıdaki görevler için yönergeler içerir:

- Bir veritabanı dosyasını SQL Server Express LocalDB 'nin daha yeni bir sürümünü kullanacak şekilde yükseltin

- SQL Server Express daha yeni bir sürümünü kullanmak için bir veritabanı dosyasını yükseltin

- Visual Studio 'da bir veritabanı dosyası ile çalışın, ancak SQL Server Express veya LocalDB 'nin daha eski bir sürümüyle uyumluluğu koruyun

- Varsayılan veritabanı altyapısını SQL Server Express yap

SQL Server Express veya LocalDB 'nin eski bir sürümü kullanılarak oluşturulmuş bir veritabanı dosyasını ( *. mdf*) içeren bir projeyi açmak Için Visual Studio 'yu kullanabilirsiniz. Ancak, projenizi Visual Studio 'da geliştirmeye devam etmek için, bu SQL Server Express veya LocalDB sürümünün Visual Studio ile aynı makineye yüklenmiş olması veya veritabanı dosyasını yükseltmeniz gerekir. Veritabanı dosyasını yükseltirseniz, SQL Server Express veya LocalDB 'nin eski sürümlerini kullanarak bu dosyaya erişemeyeceksiniz.

Ayrıca, dosyanın sürümü şu anda yüklü olan SQL Server Express veya LocalDB örneğiyle uyumlu değilse, SQL Server Express veya LocalDB 'nin önceki bir sürümüyle oluşturulmuş bir veritabanı dosyasını yükseltmeniz istenebilir. Bu sorunu çözmek için, Visual Studio dosyayı yükseltmenizi ister.

> [!IMPORTANT]
> Yükseltmeden önce veritabanı dosyasını yedeklemenizi öneririz.

> [!WARNING]
> LocalDB 2014 (V12) 32 bit içinde oluşturulan bir *. mdf* dosyasını localdb 2016 (v13) veya sonraki bir sürüme yükseltirseniz, dosyayı LocalDB 'nin 32 bit sürümünde yeniden açamazsınız.

Bir veritabanını yükseltmeden önce aşağıdaki ölçütleri göz önünde bulundurun:

- Daha eski bir sürümde ve Visual Studio 'nun daha yeni bir sürümünde projeniz üzerinde çalışmak istiyorsanız yükseltmeyin.

- Uygulamanız LocalDB yerine SQL Server Express kullanan ortamlarda kullanılacaksa, yükseltmeyin.

- LocalDB bunları kabul etmediğinden, uygulamanız uzak bağlantılar kullanıyorsa yükseltmeyin.

- Uygulamanız Internet Information Services (IIS) kullanıyorsa yükseltmeyin.

- Veritabanı uygulamalarını bir korumalı alan ortamında test etmek istiyorsanız ancak veritabanını yönetmek istemiyorsanız yükseltmeyi düşünün.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Bir veritabanı dosyasını LocalDB sürümünü kullanacak şekilde yükseltmek için

1. **Sunucu Gezgini**, **veritabanına Bağlan** düğmesini seçin.

2. **Bağlantı ekle** iletişim kutusunda, aşağıdaki bilgileri belirtin:

    - **Veri kaynağı**: `Microsoft SQL Server (SqlClient)`

    - **Sunucu adı**:

        - Varsayılan sürümü kullanmak için: `(localdb)\MSSQLLocalDB`.  Bu, hangi Visual Studio sürümünün yüklü olduğuna ve ilk LocalDB örneğinin ne zaman oluşturulduğuna bağlı olarak ProjectV12 veya ProjectV13 belirtir. SQL Server Nesne Gezgini **Mssqllocaldb** düğümü, işaret ettiği sürümü gösterir.

        - Belirli bir sürümü kullanmak için: `(localdb)\ProjectsV12` veya `(localdb)\ProjectsV13`; burada V12, LocalDB 2014 ve v13 Yereldb 2016 ' dir.

    - **Veritabanı dosyası Ekle**: birincil *. mdf* dosyasının fiziksel yolu.

    - **Mantıksal ad**: dosyayla birlikte kullanmak istediğiniz ad.

3. **Tamam** düğmesini seçin.

4. İstendiğinde, dosyayı yükseltmek için **Evet** düğmesini seçin.

    Veritabanı yükseltilir, LocalDB veritabanı altyapısına iliştirilir ve artık LocalDB 'nin eski sürümüyle uyumlu değildir.

Ayrıca, bağlantı için kısayol menüsünü açıp **Bağlantıyı Değiştir**' i seçerek LocalDB 'yi kullanmak için bir SQL Server Express bağlantısını değiştirebilirsiniz. **Bağlantıyı Değiştir** iletişim kutusunda sunucu adını `(LocalDB)\MSSQLLocalDB` olarak değiştirin. **Gelişmiş Özellikler** iletişim kutusunda, **Kullanıcı örneğinin** **false**olarak ayarlandığından emin olun.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Bir veritabanı dosyasını SQL Server Express sürümünü kullanacak şekilde yükseltmek için

1. Veritabanı bağlantısının kısayol menüsünde **Bağlantıyı Değiştir**' i seçin.

2. **Bağlantıyı Değiştir** Iletişim kutusunda **Gelişmiş** düğmesini seçin.

3. **Gelişmiş Özellikler** iletişim kutusunda sunucu adını değiştirmeden **Tamam** düğmesini seçin.

    Veritabanı dosyası, SQL Server Express geçerli sürümüyle eşleşecek şekilde yükseltilir.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Visual Studio 'da veritabanıyla çalışmak, ancak SQL Server Express uyumluluklarını sürdürmek için

- Visual Studio 'da projeyi yükseltmeden açın.

  - Projeyi çalıştırmak için **F5** tuşunu seçin.

  - Veritabanını düzenlemek için **Çözüm Gezgini** *. mdf* dosyasını açın ve veritabanınıza çalışmak için **Sunucu Gezgini** düğümünü genişletin.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Varsayılan veritabanı altyapısını SQL Server Express yapmak için

1. Menü çubuğunda **araçlar**  > **Seçenekler**' i seçin.

2. **Seçenekler** iletişim kutusunda, **veritabanı araçları** seçeneklerini genişletin ve ardından **veri bağlantıları**' nı seçin.

3. **Örnek adı SQL Server** metin kutusunda, kullanmak istediğiniz SQL Server Express veya LocalDB örneğinin adını belirtin. Örnek adlandırılmazsa, `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` belirtin.

4. **Tamam** düğmesini seçin.

    SQL Server Express, uygulamalarınız için varsayılan veritabanı altyapısı olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)
