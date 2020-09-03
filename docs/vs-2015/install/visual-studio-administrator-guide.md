---
title: Visual Studio Yönetici Kılavuzu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295912"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Yönetici Kılavuzu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [Visual Studio Yönetici Kılavuzu](/visualstudio/install/visual-studio-administrator-guide).

Her bir hedef bilgisayar [Minimum yükleme gereksinimlerini](https://visualstudio.microsoft.com/vs/older-downloads/)karşıladığı sürece, Visual Studio 2015 ' i bir ağ üzerinde dağıtabilirsiniz. Yükleme dosyasını/Layout anahtarıyla çalıştırarak ( [Visual Studio 'Nun çevrimdışı yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfasında açıklandığı gibi) ve ardından bunu yerel makineden ağ paylaşımından kopyalayarak bir ağ paylaşımının oluşturulması mümkündür. ISO kullanıyorsanız, ISO 'yı bağlayabilir ve paylaşabilir veya ISO 'yu bir ağ paylaşımında kopyalayabilirsiniz.  
  
 Bir ağ paylaşımından yüklemelerin, geldiği kaynak konumu "hatırlayın" olduğunu unutmayın. Bu, bir istemci makinenin onarımına istemcinin ilk yüklendiği ağ paylaşımının geri dönmesi gerekebilecek anlamına gelir. Kuruluşunuzda çalışan Visual Studio 2015 istemcilerini tahmin ettiğiniz yaşam süresine göre hizalanacak şekilde ağ konumunuzu dikkatle seçin.  
  
## <a name="detection-and-servicing-keys"></a>Algılama ve bakım anahtarları  
 Bir Visual Studio ürününün bir bilgisayara zaten yüklenmiş olup olmadığını saptamak için kayıt defterindeki algılama alt anahtarlarını kullanabilirsiniz. Bu algılama anahtarlarını bir yükleme ile devam etmek gerekip gerekmediğini saptamak için otomatik bir dağıtımda kullanacaksınız.  Bkz. [sistem gereksinimlerini algılama](../extensibility/internals/detecting-system-requirements.md)[sistem gereksinimlerini algılama].  
  
## <a name="avoiding-reboots"></a>Yeniden başlatmalar önleme  
 Visual Studio 'Yu dağıtmadan önce uygun Visual Studio önkoşullarını karşıladığınızdan emin olmak için yeniden başlatmaları azaltabilirsiniz. .NET Framework için, önce .NET Framework 4,6 ' i yüklemeden Visual Studio 2015 ' i dağıtırsanız, Windows 8 çalıştıran bilgisayarları yeniden başlatmanız gerekebilir.  
  
 Windows ve Android cihaz öykünmesi için, zaten Windows özelliği Hyper-V açık değilse, bilgisayarları yeniden başlatmanız gerekebilir. Web geliştirme için, Windows özelliği Web sunucunuz açık değilse, bilgisayarları yeniden başlatmanız gerekebilir. Office geliştirme için, Windows 'un Windows 'u tanımla özelliği açık değilse, bilgisayarları yeniden başlatmanız gerekebilir. Windows özelliği Web sunucunuz açık değilse, bilgisayarları yeniden başlatın. Office geliştirme için, Windows 'un Windows 'u tanımla özelliği açık değilse, bilgisayarları yeniden başlatmanız gerekebilir. Windows özelliklerini algılamayı ve yüklemeyi otomatikleştirme hakkında daha fazla bilgi edinmek için bkz. [Windows server 2008 R2 'Nin Sunucu Çekirdeği yüklemesini çalıştıran sunucuya sunucu rolü yükleme](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Hata dönüş kodları  
 Aşağıdaki tabloda önemli hata kodları listelenmektedir. Bu hata kodlarını, bir yeniden başlatmanın gerekli olup olmadığını ve yükleme başarılı olup olmadığına karar vermek için Otomasyon 'da kullanabilirsiniz. Bir hata kodu alırsanız, [Visual Studio 'Yu Yüklele](../install/install-visual-studio-2015.md) sayfasındaki sorun giderme adımlarını göz önünde bulundurun.  
  
|Kurulum durumu|Yeniden başlatma gerekli değil|Yeniden başlatma gerekiyor|Description|  
|------------------|--------------------------|----------------------|-----------------|  
|Başarılı|0x00000000 [0]|0x00000bc2 [3010]|Yükleme başarılı.|  
|Blok|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Raporlanacak tek blok "yeniden başlatma bekleniyor" ise, döndürülen değer eksik-yeniden başlatma gerekli değeridir (0x80048bc7).|  
|İptal|0x00000642 [1602]|0x80048642 [-2147187134]|Yeniden başlatma değeri döndürüldüğünde, dönüş kodu 1602 ' dir.|  
|Tamamlanmamış-yeniden başlatma gerekiyor|Yok|0x80048bc7 [-2147185721]|Yüklemenin devam edebilmesi için yeniden başlatma gerekiyor.|  
|Hata|0x00000643 [1603]|0x80048643 [-2147187133]|Yeniden başlatma değeri döndürüldüğünde, dönüş kodu 1603 ' dir.|  
  
## <a name="interactive-administrator-installer"></a>Etkileşimli yönetici yükleyicisi  
 Visual Studio yüklemesinin üstünde etkileşimli bir yükleyici oluşturuyorsanız, ilerlemeyi Visual Studio yükleyicisinden görüntüleyebilirsiniz. Visual Studio 2015 yükleyicisi, "yakma" olarak da bilinen açık kaynaklı Windows Installer XML (WiX) Chainer teknolojisine kurulmuştur. Yazma teknolojisi iki iletişim protokolünü destekler: yakma ve netfx4. Kısa bir başvuru için, lütfen [wixtoolset.org](https://wixtoolset.org/)adresindeki ExePackage öğesinin belgelerindeki protokol özniteliğinin açıklamasına bakın. Bu protokol özniteliğinin WiX açık kaynaklı uygulamasının incelenmesi, tümleştirme için gerekli olabilir.  
  
## <a name="controlling-what-is-installed"></a>Nelerin yüklü olduğunu denetleme  
 Son kullanıcılarınızın ne yükleyebileceklerini denetlemek istiyorsanız, iki seçenek vardır: yönetici dosyası yüklemesi ve komut satırı seçenekleri. Amacınız, son kullanıcılarınızın Visual Studio yükleyicisi deneyiminden neleri seçebileceğini kısıtladıysanız, yönetici dosyası yükleme ' yi seçin. Bir başlangıç yapılandırması oluşturmak, ancak son kullanıcının kendi Visual Studio yükleyicisi deneyimini seçmesini sağlamak istiyorsanız komut satırı parametrelerini seçin.  
  
 Yönetici dosyası deneyimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: katılımsız bir Visual Studio yüklemesi oluşturma ve çalıştırma](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) ve [nasıl yapılır: Visual Studio 'yu dağıttığınızda ürün anahtarlarını otomatik olarak uygulama](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Komut satırı denetimleri hakkında daha fazla bilgi için bkz. [Visual Studio 'Yu yüklemek Için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) sayfası.  
  
## <a name="specifying-customer-feedback-settings"></a>Müşteri geri bildirim ayarlarını belirtme  

Varsayılan olarak, Visual Studio yüklemesi müşteri geri bildirimlerine izin vermez. Visual Studio 'Yu, her bir bilgisayarda müşteri geri bildirimini devre dışı bırakmak için, aşağıdaki kayıt defteri anahtarının değerini "0" dizesiyle değiştirerek yapılandırabilirsiniz:  
  
**\SOFTWARE\Policies\Microsoft\VisualStudio\SQM HKEY_LOCAL_MACHINE**  
**OptIn**  
  
(Örneğin, HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SQM OPI = "0") olarak değiştirin  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu|Description|  
|-----------|-----------------|  
|[Nasıl Yapılır: Visual Studio’nun Belirli Bir Sürümünü Yükleme](../install/how-to-install-a-specific-release-of-visual-studio.md)|Geçerli sürümünün belirli yapılandırmalarının nasıl yükleneceğini açıklar  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|[Nasıl Yapılır: Katılımsız Visual Studio Yüklemesi Oluşturma ve Çalıştırma](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Katılımsız modda nasıl yükleneceğini açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|[Nasıl Yapılır: Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Birden çok makineye dağıtım yaparken Ürün anahtarlarının nasıl uygulanacağını açıklar.|  
|[Yardım Görüntüleyicisi Yönetici Kılavuzu](../ide/help-viewer-administrator-guide.md)|İnternet erişimi olan veya olmayan ağ ortamları için yerel yardım yüklemelerinin nasıl yönetileceği hakkında bilgi sağlar.|  
|[Visual Studio'yu yükleme](../install/install-visual-studio-2015.md)|' Nin nasıl yükleneceğini açıklayan konularda yönergeler ve bağlantılar sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|