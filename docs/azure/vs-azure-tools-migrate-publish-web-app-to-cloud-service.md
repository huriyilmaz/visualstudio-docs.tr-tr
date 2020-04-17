---
title: Web uygulamasını Azure Bulut Hizmeti'ne geçirin & yayımlayın
description: Visual Studio'yu kullanarak web uygulamanızı azure bulut hizmetine nasıl geçirip yayımlayacağınızı öğrenin
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: a5f918cac9d2b9e97c047e8823d7702768134336
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489681"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Nasıl yapılır: Visual Studio'dan Bir Web Uygulamasını Azure Bulut Hizmetine Geçirin ve Yayımlayın

Azure'un barındırma hizmetlerinden ve ölçekleme yeteneğinden yararlanmak için web uygulamanızı bir Azure bulut hizmetine geçirip dağıtmak isteyebilirsiniz. Yalnızca en az değişiklik gereklidir. Bu makalede, yalnızca bulut hizmetlerine dağıtma; Uygulama Hizmeti için bkz. [Azure Uygulama Hizmeti'nde bir web uygulaması dağıt.](/azure/app-service/app-service-deploy-local-git)

> [!Important]
> Bu geçiş yalnızca belirli ASP.NET, Silverlight, WCF ve WCF İş Akışı projeleri için desteklenir. ASP.NET Core projeleri için desteklenmez. Bkz. [Desteklenen Proje Şablonları.](#supported-project-templates)

## <a name="migrate-a-project-to-cloud-services"></a>Projeyi bulut hizmetlerine geçirme

1. Web uygulama projesine sağ tıklayın ve **Microsoft Azure Bulut Hizmeti Projesi'ne Dönüştür >'ı**seçin. (Çözümde zaten bir web rol projeniz varsa bu komutun görünmediğini unutmayın.)
1. Visual Studio, çözümde gerekli web rolünü içeren bir bulut hizmeti projesi oluşturur. Bu projenin adı artı sonek `.Azure`ile uygulama projesi ile aynıdır.
1. Visual Studio ayrıca **MVC** 2, MVC 3, MVC 4 ve Silverlight İş Uygulamaları için gerekli olan tüm derlemeler için Copy Local özelliğini de gerçeğe uygun olarak ayarlar. Bu özellik, dağıtım için kullanılan hizmet paketine bu derlemeleri ekler.

   > [!Important]
   > Bu web uygulaması için gerekli olan başka derlemeler veya dosyalar varsa, bu dosyaların özelliklerini el ile ayarlamanız gerekir. Bu özelliklerin nasıl ayarlanılabildiğini öğrenmek için [bkz.](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package)

### <a name="errors-and-warnings"></a>Hatalar ve uyarılar

Oluşan uyarılar veya hatalar, eksik derlemeler gibi Azure'a dağıtılamadan önce düzeltilmesi gereken sorunları gösterir.

Uygulamanızı oluşturur, bilgi işlem emülatörü kullanarak yerel olarak çalıştırın veya Azure'da yayımlarsanız, hatayı görebilirsiniz: "Belirtilen yol, dosya adı veya her ikisi de çok uzun." Bu hata, tam nitelikli Azure proje adının uzunluğunun 146 karakteri aştığını gösterir. Sorunu düzeltmek için çözümünüzü daha kısa bir yol ile farklı bir klasöre taşıyın.

Uyarılara hata olarak nasıl davranılabildiğiniz hakkında daha fazla bilgi için Visual [Studio ile Azure Bulut Hizmeti Projesini Yapılandırma'ya](vs-azure-tools-configuring-an-azure-project.md)bakın.

### <a name="test-the-migration-locally"></a>Geçişi yerel olarak test edin

1. Visual Studio **Solution Explorer'da,** eklenen bulut hizmeti projesine sağ tıklayın ve Başlangıç Projesi olarak **Ayarla'yı**seçin.
1. Azure hata ayıklama ortamını başlatmak için **Hata Ayıklama > Hata Ayıklama'yı** (F5) başlat'ı seçin. Bu ortam özellikle çeşitli Azure hizmetlerinin öykünmesini sağlar.

### <a name="use-an-azure-sql-database-for-your-application"></a>Uygulamanız için Bir Azure SQL Veritabanı kullanma

Web uygulamanız için şirket içi SQL Server veritabanı kullanan bir bağlantı dizeniz varsa, veritabanınızı Azure SQL Veritabanı'na geçirmeniz ve bağlantı dizenizi güncelleştirmeniz gerekir. Bu işlemle ilgili rehberlik için aşağıdaki konulara bakın:

- [SQL Server veritabanını buluttaki SQL Veritabanına taşıma](/azure/sql-database/sql-database-cloud-migrate)
- [Bağlanmak ve sorgulamak için Visual Studio ile .NET (C#) ve Azure SQL veritabanını kullanın.](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)

## <a name="publish-the-application-to-azure-cloud-service"></a>Uygulamayı Azure Bulut Hizmeti'nde yayımla

1. [Visual Studio'dan bir Azure uygulamasını yayımlamaya veya dağıtmaya hazırla'da](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)açıklandığı gibi Azure aboneliğinizde gerekli bulut hizmeti ve depolama hesaplarını oluşturun.
1. Visual Studio'da uygulama projesine sağ tıklayın ve **Microsoft Azure'a Yayımla'yı seçin...** (bu "Yayımla..." komutu.).
1. Görünen **Azure Uygulamasını** Yayımla'da, Azure aboneliğinizle hesabı kullanarak oturum açın ve **Sonraki >'yi **seçin.
1. Ayarlar **> Ortak Ayarlar** sekmesinde, seçtiğiniz ortam ve yapılandırmalarla birlikte **Bulut Hizmeti** açılır listesinden hedef bulut hizmetini seçin.
1. **Gelişmiş Ayarlar >** Ayarlar'da kullanılacak depolama hesabını seçin ve ardından Sonraki **>'yi **seçin.
1. **Tanılama'da,** Uygulama Öngörüleri'ne bilgi gönderip göndermemeyi seçin.
1. Özeti görüntülemek için **Sonraki >'yi** seçin ve ardından dağıtımı başlatmak için **Yayımla'yı** seçin.
1. Visual Studio, ilerlemeyi izleyebileceğiniz bir etkinlik günlüğü penceresi açar:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (İsteğe bağlı) Dağıtım işlemini iptal etmek için, etkinlik günlüğündeki satır öğesine sağ tıklayın ve **İptal et'i seçin ve kaldırın.** Bu komut dağıtım işlemini durdurur ve dağıtım ortamını Azure'dan siler. Not: Bu dağıtım ortamını dağıtıldıktan sonra kaldırmak için [Azure portalını](https://portal.azure.com)kullanmanız gerekir.
1. (İsteğe bağlı) Rol örnekleriniz başladıktan sonra Visual Studio, **Sunucu Gezgini > Bulut Hizmetleri** düğümünde dağıtım ortamını otomatik olarak gösterir. Buradan tek tek rol örneklerinin durumunu görüntüleyebilirsiniz.
1. Dağıtımdan sonra uygulamanıza erişmek için, AZURE **Etkinliği günlüğünde** URL ile birlikte **Tamamlanmış'ın** durumu göründüğünde dağıtımınızın yanındaki oku seçin. Azure'dan belirli bir web uygulaması türünü nasıl başlatılabilirsiniz hakkında ayrıntılar için aşağıdaki tabloya bakın.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Azure'da bilgi işlem emülatörve başlangıç uygulamasını kullanma

Tüm uygulama türleri, Hata Ayıklama'yı başlat (F5) **>** Hata Ayıklama'yı seçerek Visual Studio hata ayıklamaya bağlı bir tarayıcıda başlatılabilir. Boş Web Uygulaması projesinin ASP.NET, öncelikle `.aspx` uygulamanıza bir sayfa eklemeniz ve web projenizin başlangıç sayfası olarak ayarlamanız gerekir.

Aşağıdaki tablo, uygulamayı Azure'da başlatma hakkında ayrıntılı bilgi sağlar:

| Web Uygulama Türü | Azure'da Çalıştırma |
| --- | --- |
| ASP.NET Web Uygulaması<br/>(MVC 2, MVC 3, MVC 4 dahil) | **Azure Etkinliği günlüğü**için **Dağıtım** sekmesinde URL'yi seçin. |
| ASP.NET Boş Web Uygulaması | Uygulamanızda varsayılan `.aspx` bir sayfa varsa, **Azure Etkinliği günlüğüne** **dağıtım** sekmesinde URL'yi seçin. Farklı bir sayfaya gitmek için tarayıcıya aşağıdaki formun URL'sini girin:`<deployment_url>/<page_name>.aspx` |
| Silverlight Uygulama<br/>Silverlight İş Başvurusu<br/>Silverlight Navigasyon Uygulaması | Aşağıdaki URL formunu kullanarak uygulamanızın belirli sayfasına gidin:`<deployment_url>/<page_name>.aspx` |
| WCF Hizmet Başvurusu<br/>WCF İş Akışı Hizmeti Uygulaması | Dosyayı `.svc` WCF Hizmeti projenizin başlangıç sayfası olarak ayarlayın. Daha sonra`<deployment_url>/<service_file>.svc` |
| ASP.NET Dinamik Varlıklar<br/>ASP.NET Dinamik Veri Linq SQL için | Sonraki bölümde açıklandığı gibi bağlantı dizesini güncelleştirin. Sonra gidin. `<deployment_url>/<page_name>.aspx` Linq'den SQL'e için bir Azure SQL veritabanı kullanmanız gerekir. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>ASP.NET Dinamik Varlıklar için Bağlantı Dizelerini Güncelleştirme

1. Daha önce (#use-an-azuresql-database-for-your-application) açıklandığı gibi ASP.NET Dinamik Varlıklar web uygulaması için bir SQL Azure veritabanı oluşturun.
1. Azure portalından bu veritabanı için ihtiyacınız olan tabloları ve alanları ekleyin.
1. `web.config` Dosyada aşağıdaki biçimde bir bağlantı dizesi belirtin ve dosyayı kaydedin:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    SQL Azure veritabanınız için ADO.NET bağlantı dizesi ile *bağlantıString* değerini aşağıdaki gibi güncelleştirin:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Desteklenen Proje Şablonları

Bulut hizmetlerine geçirilebilen ve yayımlanabilen uygulamaların aşağıdaki tablodaki şablonlardan birini kullanması gerekir. ASP.NET Core desteklenmez.

| Şablon Grubu | Proje Şablonu |
| --- | --- |
| Web | ASP.NET Web Uygulaması (.NET Framework) |
| Web | ASP.NET MVC 2 Web Uygulaması |
| Web | ASP.NET MVC 3 Web Uygulaması |
| Web | ASP.NET MVC4 Web Uygulaması |
| Web | ASP.NET Boş Web Uygulaması (veya Site) |
| Web | ASP.NET MVC 2 Boş Web Uygulaması |
| Web | ASP.NET Dinamik Veri Varlıkları Web Uygulaması |
| Web | ASP.NET Dinamik Veri Linq SQL Web Uygulaması için |
| Silverlight | Silverlight Uygulama |
| Silverlight | Silverlight İş Başvurusu |
| Silverlight | Silverlight Navigasyon Uygulaması |
| WCF | WCF Hizmet Başvurusu |
| WCF | WCF İş Akışı Hizmeti Uygulaması |
| İş akışı | WCF İş Akışı Hizmeti Uygulaması |

## <a name="next-steps"></a>Sonraki adımlar

- [Visual Studio'dan Azure Uygulamasını Yayımlamaya veya Dağıtmaya Hazırlanın](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Adlandırılmış Kimlik Doğrulama Kimlik Bilgilerini Ayarlama.](vs-azure-tools-setting-up-named-authentication-credentials.md)
