---
title: Önyükleyici paketleri oluşturuluyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f90344c156ea6c012c6ac086ffa40bf30e78a682
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300737"
---
# <a name="creating-bootstrapper-packages"></a>Önyükleyici Paketleri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kurulum programı, Windows Installer (. msi) dosyaları ve yürütülebilir programlar gibi yeniden dağıtılabilir bileşenleri tespit etmek ve yüklemek için yapılandırılabilecek genel bir yükleyicidir. Yükleyici, önyükleyici olarak da bilinir. Bileşenin yüklenmesini yönetmek için meta verileri belirten bir XML bildirimleri kümesi aracılığıyla programlanır.  
  
 Önyükleyici önce önkoşullardan birinin zaten yüklü olup olmadığını algılar. Önkoşullar yüklü değilse, ilk olarak önyükleyici lisans sözleşmelerini gösterir. İkincisi, son kullanıcı lisans sözleşmelerini kabul ettikten sonra, yükleme Önkoşullar için başlar. Aksi takdirde, önkoşullardan bazıları algılanırsa önyükleyici yalnızca uygulama yükleyicisini başlatır.  
  
## <a name="creating-custom-packages"></a>Özel Paketler oluşturma  
 Visual Studio 'da XML düzenleyicisini kullanarak bildirimleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md) ve [nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md). Önyükleyici paketi oluşturma örneği hakkında bir örnek görmek için bkz. [Izlenecek yol: özel önyükleyici oluşturma bir gizlilik Istemi göstermek için](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Önyükleyici paketi oluşturmak için, önyükleyici bildirim oluşturucusunun bir EXE veya MSI file.to biçiminde yeniden dağıtılabilir sağlamalısınız. Ardından, Önyükleyici Bildirim Oluşturucusu aşağıdaki dosyaları oluşturur:  
  
- Paket için dilden bağımsız meta veriler içeren ürün bildirimi, Product. xml. Bu, yeniden dağıtılabilir bileşenin tüm yerelleştirilmiş sürümlerinde ortak olan meta verileri içerir.  
  
- Dile özgü meta veriler içeren Package. xml; paket bildirimi. genellikle yerelleştirilmiş hata iletileri içerir. Bir bileşen, bu bileşenin yerelleştirilmiş her sürümü için en az bir paket bildirimine sahip olmalıdır.  
  
  Bu dosyalar oluşturulduktan sonra, ürün bildirim dosyasını özel önyükleyici için adlı bir klasöre koyun. Paket bildirim dosyası, yerel ayar için adlı bir klasöre gider. Örneğin, Paket bildirim dosyası Ingilizce yeniden dağıtım için ise, dosyayı en-adlı bir klasöre koyun. Bu işlemi her yerel ayar için (Japonca için ja ve Almanca için de) yineleyin. Son özel önyükleyici paketi aşağıdaki klasör yapısına sahip olabilir.  
  
  `CustomBootstrapperPackage`  
  
  `product.xml`  
  
  `CustomBootstrapper.msi`  
  
  `de`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `en`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `ja`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  Son olarak, yeniden dağıtılabilir dosyaları önyükleyici klasörü konumuna kopyalayın. Daha fazla bilgi için bkz. [nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 veya  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Aşağıdaki kayıt defteri anahtarındaki **yol** değerinden önyükleyici klasörü konumunu da belirleyebilirsiniz:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 64 bit sistemlerde aşağıdaki kayıt defteri anahtarını kullanın:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Her yeniden dağıtılabilir bileşen, paketler dizini altındaki kendi alt klasöründe görünür. Ürün bildirimi ve yeniden dağıtılabilir dosyalar bu alt klasöre konur. Bileşen ve paket bildirimlerinin yerelleştirilmiş sürümleri, kültür adına göre adlı alt klasörlere konur.  
  
 Bu dosyalar önyükleyici klasörüne kopyalandıktan sonra, önyükleyici paketi otomatik olarak Visual Studio önkoşulları iletişim kutusunda görünür. Özel önyükleyici paketiniz görünmezse, Önkoşullar Iletişim kutusunu kapatın ve yeniden açın. Daha fazla bilgi için bkz. [Önkoşullar Iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  
  
 Aşağıdaki tabloda, önyükleyici tarafından otomatik olarak doldurulan özellikler gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|ApplicationName|Uygulamanın adı.|  
|ProcessorArchitecture|Bir yürütülebilir dosya tarafından hedeflenen platformun işlemci ve sözcük başına bit sayısı. Değerler şunlardır:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Microsoft Windows 95, Windows 98 veya Windows ME işletim sistemleri için sürüm numarası. Sürümün sözdizimi, birincil. Minor. hizmetpaketi.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 ya da Windows 7 işletim sistemleri için sürüm numarası. Sürümün sözdizimi, birincil. Minor. hizmetpaketi.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Windows Installer derlemesinin (msi. dll) sürümü yükleme sırasında çalışır.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Kullanıcının yönetici ayrıcalıkları varsa, bu özellik ayarlanır. Değerler true veya false şeklindedir.|  
|InstallMode|Yükleme modu, bileşenin nereden yüklenmesi gerektiğini gösterir. Değerler şunlardır:<br /><br /> -HomeSite-Önkoşullar, satıcının Web sitesinden yüklenir.<br />-SpecificSite-Önkoşullar seçtiğiniz konumdan yüklenir.<br />-SameSite-Önkoşullar uygulamayla aynı konumdan yüklenir.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Uygulama yüklemelerinden yeniden dağıtılabilir ayırma  
 Yeniden dağıtılabilir dosyaların Kurulum projelerinde dağıtılmasını engelleyebilirsiniz. Bunu yapmak için .NET Framework dizininizdeki RedistList klasöründe yeniden dağıtılabilir bir liste oluşturun:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Yeniden dağıtılabilir liste, şu biçimi kullanarak ad almanız gereken bir XML dosyasıdır: *Şirket adı*. *Bileşen adı*. RedistList. xml. Bu nedenle, örneğin, bileşen Acme tarafından yapılan veri öğeleri olarak çağrılırsa, Acme. Datapencere öğeleri. RedistList. xml kullanın. Yeniden dağıtılabilir listenin içeriğine bir örnek şuna benzeyebilir:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Önkoşullar Iletişim kutusu](../ide/reference/prerequisites-dialog-box.md)   
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)   
 [Yüklemeyi başlatmak için Visual Studio 2005 önyükleyici kullanın](https://go.microsoft.com/fwlink/?LinkId=107537)
