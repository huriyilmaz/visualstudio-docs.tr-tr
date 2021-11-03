---
title: Yayımlama ayarlarını içeri aktararak IIS 'de yayımlayın
description: Visual Studio bir uygulamayı IIS 'ye dağıtmak için Yayımlama profili oluşturma ve içeri aktarma
ms.date: 10/22/2021
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: baa81fc1eb735a790d6040643fa096be64858c18
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127773"
---
# <a name="get-publish-settings-from-iis-and-import-into-visual-studio"></a>IIS 'den yayımlama ayarlarını al ve Visual Studio içeri aktar

**Yayımla aracını kullanarak** yayınlama ayarlarını içeri aktarabilir ve ardından uygulamanızı dağıtabilirsiniz. Bu makalede IIS için yayımlama ayarlarını kullanırız.

bu adımlar ASP.NET ve ASP.NET Core web uygulamaları için geçerlidir.

> [!NOTE]
> Yayımlama ayarları dosyası (*\* . publishsettings*) bir yayımlama profilinden (*\* . pubxml*) farklıdır. Bir yayımlama ayarları dosyası IIS 'de oluşturulur ve ardından Visual Studio içine aktarılabilir. Visual Studio yayımlama profilini oluşturur.

## <a name="prerequisites"></a>Önkoşullar

* ASP.NET ve web geliştirme iş yüküyle [Visual Studio](https://www.visualstudio.com/downloads) yüklendi. Visual Studio zaten yüklüyse:

  *   >  **güncelleştirmeler için yardım denetle**'yi seçerek en son güncelleştirmeleri Visual Studio.
  * **Araçlar**  >  **Al araçlar ve Özellikler '** i seçerek iş yükünü ekleyin.

* sunucunuzda Windows Server 2012, Windows Server 2016 veya Windows server 2019 ' i çalıştırıyor olmanız gerekir ve [ııs Web sunucusu rolünün](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45#solution) doğru bir şekilde yüklenmiş olması gerekir (yayımlama ayarları dosyası (*\* . publishsettings*) oluşturmak için gereklidir). ASP.NET 4,5 ya da ASP.NET Core de sunucuda yüklü olmalıdır.

  * ASP.NET Core ayarlamak için, bkz. [ııs ile Windows konak ASP.NET Core](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET Core için uygulama havuzunu makalede açıklandığı gibi, **yönetilen kod olmadan** kullanmak üzere yapılandırdığınızdan emin olun.

  * ASP.NET 4,5 ayarlamak için [ASP.NET 3,5 ve 4,5 ASP.NET kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)' e bakın.

  > [!NOTE]
  > Windows ııs, yayımlama ayarlarının oluşturulmasını desteklemez. Ancak, hala Visual Studio ' deki Yayımla aracını kullanarak IIS 'de yayımlayabilirsiniz.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows sunucusuna Web Dağıtımı yükleyip yapılandırın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows sunucuda ııs 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır.

## <a name="common-issues"></a>Genel sorunlar

ilk olarak, durum bilgileri için Visual Studio çıkış penceresini kontrol edin ve hata iletilerinizi kontrol edin. Ek olarak:

- Ana bilgisayara konak adını kullanarak bağlanamıyorsanız, bunun yerine IP adresini deneyin.
- Gerekli bağlantı noktalarının uzak sunucuda açık olduğundan emin olun.
- ASP.NET Core için, ııs 'de, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok** olarak ayarlandığından emin olmanız gerekir.
- uygulamanızda kullanılan ASP.NET sürümünün sunucuda yüklü olan sürümle aynı olduğunu doğrulayın. Uygulamanız için **Özellikler** sayfasındaki sürümü görüntüleyebilir ve ayarlayabilirsiniz. Uygulamayı farklı bir sürüme ayarlamak için bu sürümün yüklü olması gerekir.
- Uygulama açılmaya çalıştıysanız, ancak bir sertifika uyarısı görürseniz, siteye güvenmeyi seçin. Uyarıyı zaten kapattıysanız, projenizdeki *. pubxml dosyasını düzenleyebilir ve şu öğeyi ekleyebilirsiniz: `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>` . Bu ayar yalnızca test amaçlıdır!
- uygulama Visual Studio başlamazsa, doğru şekilde dağıtıldığını test etmek için uygulamayı ııs 'de başlatın.