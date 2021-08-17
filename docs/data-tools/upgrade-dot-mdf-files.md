---
title: .mdf dosyalarını yükseltme
description: Veritabanı dosyasının (.mdf) yeni bir sürümünü yükledikten sonra yükseltme seçeneklerini gözden Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8a84ef3c52092feab447dfb26110129f89b1a766
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031581"
---
# <a name="upgrade-mdf-files"></a>.mdf dosyalarını yükseltme

Bu konuda, yeni bir veritabanı dosyası yükledikten sonra veritabanı dosyasını (*.mdf*) yükseltme seçenekleri Visual Studio. Aşağıdaki görevler için yönergeler içerir:

- LocalDB'nin daha yeni bir sürümünü kullanmak için veritabanı SQL Server Express yükseltme

- Veritabanı dosyasını daha yeni bir sürümü kullanmak için SQL Server Express

- Visual Studio'de bir veritabanı dosyasıyla çalışma ama SQL Server Express veya LocalDB'nin eski bir sürümüyle uyumluluğu koruma

- Varsayılan SQL Server Express altyapısını oluşturun

Visual Studio veya LocalDB'nin eski bir sürümü kullanılarak oluşturulmuş bir veritabanı dosyası (*.mdf*) içeren bir projeyi açmak için SQL Server Express kullanabilirsiniz. Ancak projenizi Visual Studio'de geliştirmeye devam etmek için SQL Server Express veya LocalDB sürümünün Visual Studio makinede yüklü olması veya veritabanı dosyasını yükseltmeniz gerekir. Veritabanı dosyasını yükseltersiniz, eski SQL Server Express veya LocalDB sürümlerini kullanarak dosyaya erişesiniz.

Dosyanın sürümü şu anda yüklü olan SQL Server Express veya LocalDB örneğiyle uyumlu değilse, önceki bir SQL Server Express veya LocalDB sürümü aracılığıyla oluşturulmuş bir veritabanı dosyasını yükseltmeniz de istenebilirsiniz. Sorunu çözmek için Visual Studio dosyayı yükseltmeniz istenir.

> [!IMPORTANT]
> Yükseltmeden önce veritabanı dosyasını yeniden yüklemenizi öneririz.

> [!WARNING]
> LocalDB 2014 (V12) 32 bit'te oluşturulan *bir .mdf* dosyasını LocalDB 2016 (V13) veya sonraki bir sürümüne yükseltecek olursanız, dosyayı LocalDB'nin 32 bit sürümünde yeniden açasınız.

Veritabanını yükseltmeden önce aşağıdaki ölçütleri göz önünde oluşturun:

- Projeniz üzerinde hem eski hem de daha yeni bir sürümde çalışmak için yükseltme Visual Studio.

- Uygulamanız LocalDB yerine SQL Server Express ortamlarda kullanılacaksa yükseltmeyin.

- LocalDB bunları kabul etmey olduğundan, uygulamanız uzak bağlantılar kullanıyorsa yükseltmeyin.

- Uygulamanız Internet Information Services (IIS) bağlı ise yükseltmeyin.

- Korumalı alan ortamında veritabanı uygulamalarını test etmek ancak veritabanını yönetmek istemiyorsanız yükseltmeyi göz önünde bulundurabilirsiniz.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Bir veritabanı dosyasını LocalDB sürümünü kullanmak üzere yükseltmek için

1. Bu **Sunucu Gezgini** veritabanına **Bağlan düğmesini** seçin.

2. Bağlantı **Ekle iletişim** kutusunda aşağıdaki bilgileri belirtin:

    - **Veri Kaynağı:**`Microsoft SQL Server (SqlClient)`

    - **Sunucu Adı:**

        - Varsayılan sürümü kullanmak için: `(localdb)\MSSQLLocalDB` .  Bu, hangi sürümün yüklü olduğuna ve ilk LocalDB örneğinin ne zaman Visual Studio ProjectV12 veya ProjectV13'ü belirtir. SQL Server Nesne Gezgini **MSSQLLocalDB**  düğümü, hangi sürümü işaret ediyor olduğunu gösterir.

        - Belirli bir sürümü kullanmak için veya `(localdb)\ProjectsV12` `(localdb)\ProjectsV13` burada V12 LocalDB 2014, V13 ise LocalDB 2016'dır.

    - **Bir veritabanı dosyası ekleme:** Birincil *.mdf* dosyasının fiziksel yolu.

    - **Mantıksal Ad:** Dosyayla birlikte kullanmak istediğiniz ad.

3. **Tamam** düğmesini seçin.

4. İstendiğinde, dosyayı yükseltmek **için** Evet düğmesini seçin.

    Veritabanı yükseltilir, LocalDB veritabanı altyapısına iliştirilir ve artık LocalDB'nin eski sürümüyle uyumlu değildir.

Ayrıca bağlantının kısayol menüsünü SQL Server Express sonra Bağlantıyı Değiştir'i seçerek yerel bir bağlantıyı LocalDB'yi kullanmak üzere **değiştirebilirsiniz.** Bağlantıyı **Değiştir iletişim** kutusunda sunucu adını olarak değiştirebilirsiniz. `(LocalDB)\MSSQLLocalDB` Gelişmiş Özellikler **iletişim kutusunda** Kullanıcı Örneği'nin False **olarak ayarlanmış** olduğundan emin **olun.**

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Bir veritabanı dosyasını SQL Server Express yükseltmek için

1. Veritabanı bağlantısının kısayol menüsünde Bağlantıyı **Değiştir'i seçin.**

2. Bağlantıyı **Değiştir iletişim** kutusunda Gelişmiş **düğmesini** seçin.

3. Gelişmiş **Özellikler iletişim** kutusunda, sunucu adını **değiştirmeden** Tamam düğmesini seçin.

    Veritabanı dosyası, veritabanının geçerli sürümüyle eş SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Veritabanında çalışmak ama Visual Studio uyumluluğunu korumak SQL Server Express

- Bu Visual Studio yükseltmeden projeyi açın.

  - Projeyi çalıştırmak için **F5 anahtarını** seçin.

  - Veritabanını düzenlemek için , *.mdf* dosyasını **Çözüm Gezgini** açın ve veritabanındaki **Sunucu Gezgini** ile çalışacak şekilde genişletin.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Varsayılan SQL Server Express altyapısını oluşturmak için

1. Menü çubuğunda Araçlar **Seçenekler'i**  >  **seçin.**

2. Seçenekler iletişim **kutusunda** Veritabanı Araçları seçeneklerini **genişletin ve** Veri Bağlantıları'ı **seçin.**

3. SQL Server **Örnek Adı** metin kutusunda, kullanmak istediğiniz SQL Server Express veya LocalDB örneğinin adını belirtin. Örnek adlandırılmış değilse `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` belirtin.

4. **Tamam** düğmesini seçin.

    SQL Server Express, uygulamalarınız için varsayılan veritabanı altyapısı olacak.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)
