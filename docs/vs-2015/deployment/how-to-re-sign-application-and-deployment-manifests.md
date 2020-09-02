---
title: 'Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697556"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Nasıl yapılır: Uygulama ve Dağıtım Bildirimlerini Yeniden İmzalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama bildiriminde Windows Forms uygulamalar, Windows Presentation Foundation uygulamalar (XBAP) veya Office çözümleri için dağıtım özelliklerinde değişiklikler yaptıktan sonra, hem uygulama hem de dağıtım bildirimlerini bir sertifikayla yeniden imzalamanız gerekir. Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklü olmamasını sağlamaya yardımcı olur.  
  
 Bildirimleri yeniden imzalayabileceğiniz başka bir senaryo ise müşterilerinizin uygulama ve dağıtım bildirimlerini kendi sertifikasıyla imzalamasını ister.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini yeniden imzalama  
 Bu yordam, uygulama bildirimi dosyanızda (. manifest) daha önce değişiklikler yapmış olduğunuzu varsayar. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım özelliklerini değiştirme](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım bildirimlerini Mage.exe ile yeniden imzalamak için  
  
1. Bir **Visual Studio komut istemi** penceresi açın.  
  
2. Dizinleri imzalamak istediğiniz bildirim dosyalarını içeren klasör olarak değiştirin.  
  
3. Uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. ManifestFileName değerini bildirim dosyanızın adıyla ve uzantısıyla değiştirin. Sertifikayı sertifika dosyasının göreli veya tam yoluyla değiştirin ve parolayı sertifika parolasıyla değiştirin.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir eklenti, bir Windows form uygulaması veya bir Windows Presentation Foundation tarayıcı uygulaması için bir uygulama bildirimini imzalamak üzere aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikaların üretim ortamlarına dağıtılması önerilmez.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Dağıtım bildirimi dosyasını güncelleştirmek ve imzalamak için, önceki adımda olduğu gibi yer tutucu adlarını değiştirerek aşağıdaki komutu yazın.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir Excel eklentisi, Windows Forms uygulaması veya bir Windows Presentation Foundation tarayıcı uygulaması için bir dağıtım bildirimini güncelleştirmek ve imzalamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. İsteğe bağlı olarak, ana dağıtım bildirimini ( \\ *appname*. Application) sürüm dağıtım dizininize (publish\Application Files \\ *appname*\*Version*) kopyalayın.  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini güncelleştirme ve yeniden imzalama  
 Bu yordam, uygulama bildirimi dosyanızda (. manifest) daha önce değişiklikler yapmış olduğunu, ancak güncelleştirilmiş başka dosyalar olduğunu varsayar. Dosyalar güncelleştirilirken, dosyayı temsil eden karma değeri de güncelleştirilmeleri gerekir.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım bildirimlerini Mage.exe ile güncelleştirmek ve yeniden imzalamak için  
  
1. Bir **Visual Studio komut istemi** penceresi açın.  
  
2. Dizinleri imzalamak istediğiniz bildirim dosyalarını içeren klasör olarak değiştirin.  
  
3. Yayımla çıkış klasöründeki dosyalardan. deploy dosya uzantısını kaldırın.  
  
4. Uygulama bildirimini güncelleştirilmiş dosyalar için yeni karmalarla güncelleştirmek ve uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. ManifestFileName değerini bildirim dosyanızın adıyla ve uzantısıyla değiştirin. Sertifikayı sertifika dosyasının göreli veya tam yoluyla değiştirin ve parolayı sertifika parolasıyla değiştirin.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir eklenti, bir Windows form uygulaması veya bir Windows Presentation Foundation tarayıcı uygulaması için bir uygulama bildirimini imzalamak üzere aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikaların üretim ortamlarına dağıtılması önerilmez.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Dağıtım bildirimi dosyasını güncelleştirmek ve imzalamak için, önceki adımda olduğu gibi yer tutucu adlarını değiştirerek aşağıdaki komutu yazın.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Örneğin, bir Excel eklentisi, Windows Forms uygulaması veya bir Windows Presentation Foundation tarayıcı uygulaması için bir dağıtım bildirimini güncelleştirmek ve imzalamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Uygulama ve dağıtım bildirim dosyaları dışında. deploy dosya uzantısını dosyalara geri ekleyin.  
  
7. İsteğe bağlı olarak, ana dağıtım bildirimini ( \\ *appname*. Application) sürüm dağıtım dizininize (publish\Application Files \\ *appname*\*Version*) kopyalayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Nasıl yapılır: ClickOnce uygulamaları için bir Istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Nasıl yapılır: ClickOnce Güven İstemi Davranışını Yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
