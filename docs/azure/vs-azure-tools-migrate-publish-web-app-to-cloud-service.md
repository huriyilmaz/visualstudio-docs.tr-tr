---
title: Web uygulamasını bulut hizmetine geçirme ve yayımlama
description: Visual Studio kullanarak web uygulamalarınızı azure bulut hizmetine geçirmeyi ve yayımlamayı Visual Studio
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 28403c0d33eb9e1076b334a977deaecf6a0a99801a87a33edbcb25f7c9aa7b2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121456250"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Nasıl yapılır: Web uygulamasını azure bulut hizmetine geçirme ve yayımlama Visual Studio

Azure'ın barındırma hizmetlerinden ve ölçeklendirme becerilerinden yararlanmak için, web uygulamanızı bir Azure bulut hizmetine geçirmek ve dağıtmak iyi olabilir. Yalnızca en az değişiklik gereklidir. Bu makale yalnızca bulut hizmetleri için dağıtıma kapsar; Daha App Service için [bkz. Web uygulamasını Azure App Service.](/azure/app-service/app-service-deploy-local-git)

> [!Important]
> Bu geçiş yalnızca belirli ASP.NET, WCF ve WCF İş Akışı projeleri için de destekleniyor. Tek bir proje için ASP.NET Core değildir. Bkz. [Desteklenen Project Şablonları.](#supported-project-templates)

## <a name="migrate-a-project-to-cloud-services"></a>Projeyi bulut hizmetlerine geçirme

1. Çözüm düğümüne sağ tıklayın ve **Ekle'> Yeni Project... öğesini** seçin ve mevcut çözüme yeni bir Azure Bulut Hizmeti **(klasik)** projesi ekleyin.
1. Yeni **Bulut Microsoft Azure (klasik) iletişim kutusunda,** projeye rol eklemeden Tamam'a tıklayın.
1. Yeni eklenen proje altındaki roller düğümüne sağ tıklayın ve Cloud Services... içinde Web Rolü **Project Ekle'yi seçin.**
1. Rol **Rolü Project** iletişim kutusunda, web rolü olarak ilişkilendirmek istediğiniz projeyi seçin.

   > [!Important]
   > Bu web uygulaması için gerekli olan başka derlemeler veya dosyalarınız varsa, bu dosyaların özelliklerini el ile ayarlamalısınız. Bu özellikleri ayarlama hakkında bilgi için bkz. [Hizmet Paketine Dosya Dahil Edin.](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package)

### <a name="errors-and-warnings"></a>Hatalar ve uyarılar

Oluşan uyarılar veya hatalar, eksik derlemeler gibi Azure'a dağıtmadan önce düzeltilen sorunları gösterir.

Uygulamanızı derlemek, işlem öykünücüsünü kullanarak yerel olarak çalıştırmak veya Azure'da yayımlamak için şu hatayı alabilirsiniz: "Belirtilen yol, dosya adı veya her ikisi de çok uzun." Bu hata, tam Azure proje adının uzunluğunun 146 karakterden uzun olduğunu gösterir. Sorunu düzeltmek için çözümlerinizi daha kısa bir yol ile farklı bir klasöre taşımanız gerekir.

Uyarılara hata olarak davranma hakkında daha fazla bilgi için bkz. [Azure Cloud Service Project'yi Visual Studio.](vs-azure-tools-configuring-an-azure-project.md)

### <a name="test-the-migration-locally"></a>Geçişi yerel olarak test etmek

1. Bu Visual Studio **Çözüm Gezgini,** eklenen bulut hizmeti projesine sağ tıklayın ve Başlangıç Olarak **Ayarla'yı Project.**
1. Azure **hata ayıklama > başlatmak için Hata Ayıklamayı** Başlat (F5) öğesini seçin. Bu ortam özellikle çeşitli Azure hizmetlerinin öykünmelerini sağlar.

### <a name="use-an-azure-sql-database-for-your-application"></a>Uygulamanıza Azure SQL Veritabanı bir uygulama kullanma

Web uygulamanıza şirket içi SQL Server veritabanı kullanan bir bağlantı dizeniz varsa, veritabanınızı bunun yerine Azure SQL Veritabanı'ye geçirmeniz ve bağlantı dizenizi güncelleştirmeniz gerekir. Bu işlemle ilgili rehberlik için aşağıdaki konulara bakın:

- [SQL Server veritabanını buluttaki SQL Veritabanına taşıma](/azure/sql-database/sql-database-cloud-migrate)
- [.NET (C#) ile veritabanına Visual Studio azure veritabanına bağlanmak ve sorgulamak SQL kullanın.](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)

## <a name="publish-the-application-to-azure-cloud-service"></a>Uygulamayı Azure Bulut Hizmeti'ne yayımlama

1. Azure aboneliğinize gerekli bulut hizmeti ve depolama hesaplarını, Azure'dan bir Azure uygulaması yayımlamaya veya dağıtmaya hazırlama [konusunda açıklandığı gibi Visual Studio.](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
1. Bu Visual Studio, uygulama projesine sağ tıklayın ve **Microsoft Azure...'de yayımla...'yı** seçin (bu, "Yayımla..." komutu.).
1. Görüntülenen **Azure Uygulamasını Yayımla'da,** Azure aboneliğiniz ile hesabı kullanarak oturum açın ve Sonraki **adım'ı >.**
1. Ayarlar > **Common Ayarlar** sekmesinde, seçtiğiniz ortam ve yapılandırmalarla birlikte  Bulut Hizmeti açılan listesinden hedef bulut hizmetini seçin.
1. Gelişmiş **Ayarlar >'Ayarlar** altında, kullanmak üzere depolama hesabını seçin ve ardından **İleri'yi >.**
1. **Tanılama'da,** Application Analizler'a bilgi gönderip gönder Analizler.
1. Özeti **görüntülemek >sonraki** adım'ı ve ardından Dağıtımı başlatmak için **Yayımla'yı** seçin.
1. Visual Studio ilerlemeyi takip etmek için bir etkinlik günlüğü penceresi açar:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (İsteğe bağlı) Dağıtım işlemini iptal etmek için etkinlik günlüğünde satır öğesini sağ tıklatın ve İptal'i seçin **ve öğesini kaldırın.** Bu komut dağıtım işlemini durdurur ve dağıtım ortamını Azure'dan siler. Not: Dağıtıldıktan sonra bu dağıtım ortamını kaldırmak için [Azure portal.](https://portal.azure.com)
1. (İsteğe bağlı) Rol örnekleriniz başlatıldıktan sonra, Visual Studio otomatik olarak dağıtım ortamını Sunucu Gezgini > Cloud Services **gösterir.** Buradan tek tek rol örneklerinin durumunu görüntüabilirsiniz.
1. Dağıtımdan sonra uygulamanıza erişmek **için, Azure** Etkinlik günlüğünde URL ile birlikte Tamamlandı durumu göründüğünde dağıtımın yanındaki oku seçin.  Azure'dan belirli bir web uygulaması türünü başlatma hakkında ayrıntılı bilgi için aşağıdaki tabloya bakın.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Azure'da işlem öykünücüsünü kullanma ve uygulamayı başlatma

Hata Ayıklamayı Başlat (F5) seçerek Visual Studio hata ayıklayıcısına **bağlı bir tarayıcıda >** başlatabilirsiniz. Boş ASP.NET Uygulaması projesiyle, önce uygulamanıza bir sayfa eklemeniz ve bunu web projenizin başlangıç sayfası `.aspx` olarak ayarlamanız gerekir.

Aşağıdaki tabloda, Uygulamayı Azure'da başlatmayla ilgili ayrıntılar yer alır:

| Web Uygulaması Türü | Azure'da çalıştırma |
| --- | --- |
| ASP.NET Web Uygulaması<br/>(MVC 2, MVC 3, MVC 4 dahil) | Azure Etkinlik günlüğü **için Dağıtım** sekmesinde **URL'yi seçin.** |
| ASP.NET Boş Web Uygulaması | Uygulamanıza varsayılan bir `.aspx` sayfanız varsa, Azure Etkinlik günlüğünün **Dağıtım** sekmesindeKI **URL'yi seçin.** Farklı bir sayfaya gitmek için tarayıcıda aşağıdaki formun URL'sini girin: `<deployment_url>/<page_name>.aspx` |
| WCF Hizmet Uygulaması<br/>WCF İş Akışı Hizmeti Uygulaması | Dosyayı `.svc` WCF Hizmeti projenizin başlangıç sayfası olarak ayarlayın. Ardından şu sayfaya gidin: `<deployment_url>/<service_file>.svc` |
| ASP.NET Dinamik Varlıklar<br/>ASP.NET Dinamik Veri Linq to SQL | Bağlantı dizesini sonraki bölümde açıklandığı gibi güncelleştirin. Ardından, 'a `<deployment_url>/<page_name>.aspx` gidin. Linq'in SQL azure veritabanı SQL gerekir. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Dinamik Varlıklar için bağlantı ASP.NET güncelleştirme

1. Daha önce SQL Azure açıklandığı gibi ASP.NET Dinamik Varlıklar web uygulaması için (#use-an-azuresql-database-for-your-application) bir veritabanı oluşturun.
1. Bu veritabanı için ihtiyacınız olan tabloları ve alanları veri Azure portal.
1. Dosyada aşağıdaki biçimde bir `web.config` bağlantı dizesi belirtin ve dosyayı kaydedin:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    *connectionString değerini aşağıdaki* gibi ADO.NET veritabanınız için SQL Azure dizesiyle güncelleştirin:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Desteklenen Project Şablonları

Bulut hizmetlerinden geçirile ve yayımlana uygulamalar aşağıdaki tabloda yer alan şablonlardan birini kullandır. ASP.NET Core desteklenmiyor.

| Şablon Grubu | Proje Şablonu |
| --- | --- |
| Web | ASP.NET Web Uygulaması (.NET Framework) |
| Web | ASP.NET MVC 2 Web Uygulaması |
| Web | ASP.NET MVC 3 Web Uygulaması |
| Web | ASP.NET MVC4 Web Uygulaması |
| Web | ASP.NET Boş Web Uygulaması (veya Site) |
| Web | ASP.NET MVC 2 Boş Web Uygulaması |
| Web | ASP.NET Dinamik Veri Varlıkları Web Uygulaması |
| Web | ASP.NET Dinamik Veri Linq to SQL Web Uygulaması |
| WCF | WCF Hizmet Uygulaması |
| WCF | WCF İş Akışı Hizmeti Uygulaması |
| İş akışı | WCF İş Akışı Hizmeti Uygulaması |

## <a name="next-steps"></a>Sonraki adımlar

- [Visual Studio bir Azure uygulaması yayımlamaya veya dağıtmaya hazırlanma](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Adlandırılmış kimlik doğrulama kimlik bilgileri ayarlanıyor](vs-azure-tools-setting-up-named-authentication-credentials.md).
