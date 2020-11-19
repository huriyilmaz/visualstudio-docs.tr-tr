---
title: Web uygulamasını bir bulut hizmetine geçirme ve yayımlama
description: Visual Studio 'Yu kullanarak Web uygulamanızı bir Azure bulut hizmetine geçirmeyi ve yayımlamayı öğrenin
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c9d689ddca7b6f1b0c02f89c7afb82392e8a58af
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902356"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Nasıl yapılır: bir Web uygulamasını Visual Studio 'dan Azure bulut hizmeti 'ne geçirme ve yayımlama

Azure 'un barındırma hizmetleri ve ölçeklendirme özelliğinden yararlanmak için Web uygulamanızı geçirmek ve Azure bulut hizmetine dağıtmak isteyebilirsiniz. Yalnızca en az sayıda değişiklik gereklidir. Bu makalede yalnızca bulut hizmetlerine dağıtım ele alınmaktadır; App Service için bkz. [Azure App Service Web uygulaması dağıtma](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Bu geçiş yalnızca belirli ASP.NET, WCF ve WCF Iş akışı projeleri için desteklenir. ASP.NET Core projeleri için desteklenmez. Bkz. [desteklenen proje şablonları](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Projeyi bulut hizmetlerine geçirme

1. Çözüm düğümüne sağ tıklayın ve **> yeni proje Ekle...** öğesini seçin ve var olan çözüme yeni bir **Azure bulut hizmeti (klasik)** projesi ekleyin.
1. **Yeni Microsoft Azure bulut hizmeti (klasik)** iletişim kutusunda, projeye rol eklemeden Tamam ' a tıklayın.
1. Yeni eklenen Cloud Services projesi altındaki Roller düğümüne sağ tıklayın ve **çözümdeki web rolü projesi Ekle...** seçeneğini belirleyin.
1. **Rol projesiyle ilişkilendir** iletişim kutusunda, bir Web rolü olarak ilişkilendirmek istediğiniz projeyi seçin.

   > [!Important]
   > Bu Web uygulaması için gerekli olan başka derlemeleriniz veya dosyalarınız varsa, bu dosyaların özelliklerini el ile ayarlamanız gerekir. Bu özellikleri ayarlama hakkında daha fazla bilgi için bkz. [hizmet paketine dosya ekleme](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Hatalar ve uyarılar

Oluşan herhangi bir uyarı veya hata, eksik derlemeler gibi Azure 'a dağıtılmadan önce düzeltilme sorunları olduğunu gösterir.

Uygulamanızı derleyin, işlem öykünücüsünü kullanarak yerel olarak çalıştırın veya Azure 'da yayımlayın, şu hatayı görebilirsiniz: "belirtilen yol, dosya adı veya her ikisi çok uzun." Bu hata, tam Azure proje adının uzunluğunun 146 karakteri aştığını gösterir. Sorunu düzeltmek için çözümünüzü daha kısa bir yola sahip farklı bir klasöre taşıyın.

Uyarıları hata olarak işleme hakkında daha fazla bilgi için bkz. [Visual Studio Ile Azure bulut hizmeti projesi yapılandırma](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Geçişi yerel olarak test etme

1. Visual Studio **Çözüm Gezgini**, eklenen bulut hizmeti projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.
1. Azure hata ayıklama ortamını başlatmak için hata ayıklamayı Başlat (F5) **> hata ayıkla** ' yı seçin. Bu ortam özellikle çeşitli Azure hizmetlerinin öykünmesinin benzetimini sağlar.

### <a name="use-an-azure-sql-database-for-your-application"></a>Uygulamanız için bir Azure SQL veritabanı kullanın

Web uygulamanız için bir şirket içi SQL Server veritabanı kullanan bir bağlantı dizeniz varsa, veritabanınızı Azure SQL veritabanı 'na geçirmeniz ve Bağlantı dizenizi güncelleştirmeniz gerekir. Bu işlemle ilgili rehberlik için aşağıdaki konulara bakın:

- [SQL Server veritabanını buluttaki SQL Veritabanına taşıma](/azure/sql-database/sql-database-cloud-migrate)
- [Azure SQL veritabanı ile bağlantı kurmak ve sorgulamak Için Visual Studio ile .net (C#) kullanın](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Uygulamayı Azure bulut hizmeti 'nde yayımlayın

1. [Visual Studio 'dan bir Azure uygulaması yayımlamaya veya dağıtmaya hazırlanma](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)bölümünde açıklandığı gibi, Azure aboneliğinizde gerekli bulut hizmeti ve depolama hesaplarını oluşturun.
1. Visual Studio 'da uygulama projesine sağ tıklayın ve **Microsoft Azure..** . ("Yayımla..." öğesinden farklı Yayımla ' yı seçin. komutu.).
1. Görüntülenen **Azure uygulamasını Yayımla** ' da, Azure aboneliğinizdeki hesabı kullanarak oturum açın ve **Ileri >' yi** seçin.
1. **Ayarlar > ortak ayarlar** sekmesinde, **bulut hizmeti** açılır listesinden hedef bulut hizmetini seçtiğiniz ortam ve konfigürasyonlarla birlikte seçin.
1. **Ayarlar > Gelişmiş ayarlar**' da, kullanılacak depolama hesabını seçin ve ardından **İleri >**' yi seçin.
1. **Tanılama** bölümünde Application Insights bilgi gönderileceğini seçin.
1. Bir özeti görüntülemek için **ileri >** ' yi seçin ve sonra dağıtımı başlatmak için **Yayımla** ' yı seçin.
1. Visual Studio, ilerlemeyi izleyebileceğiniz bir etkinlik günlüğü penceresi açar:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. Seçim Dağıtım işlemini iptal etmek için etkinlik günlüğündeki satır öğesine sağ tıklayın ve **iptal ve Kaldır**' ı seçin. Bu komut dağıtım sürecini durduruyor ve dağıtım ortamını Azure 'dan siler. Note: dağıtıldıktan sonra bu dağıtım ortamını kaldırmak için [Azure Portal](https://portal.azure.com)kullanmanız gerekir.
1. Seçim Rol örneklerinizin başlatılmasından sonra Visual Studio, **Sunucu Gezgini > Cloud Services** düğümünde dağıtım ortamını otomatik olarak gösterir. Buradan, tek tek rol örneklerinin durumunu görüntüleyebilirsiniz.
1. Dağıtımdan sonra uygulamanıza erişmek için, **Azure etkinlik GÜNLÜĞÜNDE** URL Ile birlikte **tamamlandı** durumu görüntülendiğinde dağıtımınızın yanındaki oku seçin. Azure 'dan belirli bir Web uygulaması türünün nasıl başlatılacağı hakkındaki ayrıntılar için aşağıdaki tabloya bakın.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>İşlem öykünücüsünü kullanma ve Azure 'da uygulamayı başlatma

Tüm uygulama türleri Visual Studio hata ayıklayıcısına bağlı bir tarayıcıda başlatılabilir **> hata ayıklamayı Başlat** (F5) seçeneğini belirleyebilirsiniz. ASP.NET boş bir Web uygulaması projesiyle, önce `.aspx` uygulamanıza bir sayfa eklemeniz ve bunu Web projeniz için başlangıç sayfası olarak ayarlamanız gerekir.

Aşağıdaki tabloda, uygulamayı Azure 'da başlatma ile ilgili ayrıntılar verilmiştir:

| Web uygulaması türü | Azure 'da çalıştırma |
| --- | --- |
| ASP.NET Web uygulaması<br/>(MVC 2, MVC 3, MVC 4 dahil) | **Azure etkinlik günlüğü** için **dağıtım** sekmesinde URL 'yi seçin. |
| ASP.NET boş Web uygulaması | Uygulamanızda varsayılan bir sayfanız varsa `.aspx` , **Azure etkinlik günlüğü** için **dağıtım** sekmesinden URL 'yi seçin. Farklı bir sayfaya gitmek için, tarayıcıda aşağıdaki formun URL 'sini girin: `<deployment_url>/<page_name>.aspx` |
| WCF hizmeti uygulaması<br/>WCF İş Akışı Hizmeti Uygulaması | `.svc`WCF hizmeti projeniz için başlangıç sayfası olarak dosyayı ayarlayın. Sonra şuraya gidin `<deployment_url>/<service_file>.svc` |
| ASP.NET dinamik varlıkları<br/>ASP.NET dinamik veri LINQ to SQL | Bağlantı dizesini, sonraki bölümde açıklandığı gibi güncelleştirin. Sonra öğesine gidin `<deployment_url>/<page_name>.aspx` . LINQ to SQL için bir Azure SQL veritabanı kullanmanız gerekir. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>ASP.NET dinamik varlıkları için bağlantı dizesini güncelleştirme

1. Daha önce açıklandığı gibi bir ASP.NET Dynamic Entities Web uygulaması için bir SQL Azure veritabanı oluşturun (#use-a-azuresql----------veritabanı).
1. Bu veritabanı için ihtiyaç duyduğunuz tablo ve alanları Azure portal ekleyin.
1. Dosyada aşağıdaki biçimde bir bağlantı dizesi belirtin `web.config` ve dosyayı kaydedin:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    *ConnectionString* değerini SQL Azure veritabanınız için ADO.NET bağlantı dizesiyle güncelleştirin:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Desteklenen proje şablonları

Cloud Services 'a geçirilebilecek ve yayımlanmakta olabilecek uygulamalar aşağıdaki tabloda yer alan şablonlardan birini kullanmalıdır. ASP.NET Core desteklenmez.

| Şablon grubu | Proje Şablonu |
| --- | --- |
| Web | ASP.NET Web uygulaması (.NET Framework) |
| Web | ASP.NET MVC 2 Web uygulaması |
| Web | ASP.NET MVC 3 Web uygulaması |
| Web | ASP.NET MVC4 Web uygulaması |
| Web | ASP.NET boş Web uygulaması (veya sitesi) |
| Web | ASP.NET MVC 2 boş Web uygulaması |
| Web | ASP.NET dinamik veri varlıkları Web uygulaması |
| Web | ASP.NET dinamik veri LINQ to SQL Web uygulaması |
| WCF | WCF hizmeti uygulaması |
| WCF | WCF İş Akışı Hizmeti Uygulaması |
| İş akışı | WCF İş Akışı Hizmeti Uygulaması |

## <a name="next-steps"></a>Sonraki adımlar

- [Visual Studio 'dan bir Azure uygulaması yayımlamaya veya dağıtmaya hazırlanma](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Adlandırılmış kimlik doğrulama kimlik bilgileri ayarlanıyor](vs-azure-tools-setting-up-named-authentication-credentials.md).
