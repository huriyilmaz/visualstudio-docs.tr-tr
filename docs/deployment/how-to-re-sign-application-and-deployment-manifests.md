---
title: 'Nasıl yapılır: Uygulama ve Dağıtım Bildirimlerini Yeniden İmzala | Microsoft Dokümanlar'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649173"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Nasıl yapilir: Uygulama ve dağıtım bildirimlerini yeniden imzalama
Windows Forms uygulamaları, Windows Presentation Foundation uygulamaları (xbap) veya Office çözümleri için uygulama bildiriminde dağıtım özelliklerinde değişiklik yaptıktan sonra, hem uygulama hem de dağıtım bildirimlerini bir sertifikayla yeniden imzalamanız gerekir. Bu işlem, değiştirilmiş dosyaların son kullanıcı bilgisayarlara yüklenmemesini sağlamaya yardımcı olur.

 Bildirimleri yeniden imzalayabileceğiniz başka bir senaryo da, müşterilerinizin uygulama ve dağıtım bildirimlerini kendi sertifikalarıyla imzalamak istemeleridir.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Uygulama ve Dağıtım Bildirimlerini Yeniden İmzalayın
 Bu yordam, uygulama bildirimi dosyanızda (*.manifest)* değişiklik yaptığınızı varsayar. Daha fazla bilgi için [bkz: Dağıtım özelliklerini değiştirme.](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım bildirimlerini Mage.exe ile yeniden imzalamak için

1. Visual **Studio Komut İstem** penceresi açın.

2. Dizinleri imzalamak istediğiniz bildirim dosyalarını içeren klasörle değiştirin.

3. Başvuru bildirimi dosyasını imzalamak için aşağıdaki komutu yazın. *ManifestFileName'i* bildirim dosyanızın adı ve uzantısı ile değiştirin. *Sertifikayı* sertifika dosyasının göreli veya tam nitelikli yolu ile değiştirin ve *Parola'yı* sertifikanın parolasıyla değiştirin.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Örneğin, bir eklenti, windows form uygulaması veya Windows Presentation Foundation tarayıcı uygulaması için bir uygulama bildirimini imzalamak için aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikalar, üretim ortamlarına dağıtım için önerilmez.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Yer tutucu adlarını önceki adımdaki gibi değiştirerek dağıtım bildirimi dosyasını güncelleştirmek ve imzalamak için aşağıdaki komutu yazın.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Örneğin, excel eklentisi, Windows Forms uygulaması veya Windows Presentation Foundation tarayıcı uygulaması için dağıtım bildirimini güncelleştirmek ve imzalamak için aşağıdaki komutu çalıştırabilirsiniz.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. İsteğe bağlı olarak, ana dağıtım bildirimini *(uygulama>.application\\\<yayımla)* sürüm dağıtım dizininize kopyalayın (*yayım\Uygulama Dosyaları\\\<>_\<sürüm>). *

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini güncelleştirin ve yeniden imzalayın
 Bu yordam, uygulama bildirimi dosyanızda zaten değişiklikler yaptığınızı varsayar (*.manifest*), ancak güncelleştirilen başka dosyalar da vardır. Dosyalar güncelleştirildiğinde, dosyayı temsil eden karma nın da güncelleştirilmelidir.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım bildirimlerini Mage.exe ile güncellemek ve yeniden imzalamak için

1. Visual **Studio Komut İstem** penceresi açın.

2. Dizinleri imzalamak istediğiniz bildirim dosyalarını içeren klasörle değiştirin.

3. *.deploy* dosya uzantısını yayımlama çıktıklasöründeki dosyalardan kaldırın.

4. Güncelleştirilmiş dosyalar için yeni hashes ile uygulama bildirimini güncelleştirmek ve uygulama bildirimi dosyasını imzalamak için aşağıdaki komutu yazın. *ManifestFileName'i* bildirim dosyanızın adı ve uzantısı ile değiştirin. *Sertifikayı* sertifika dosyasının göreli veya tam nitelikli yolu ile değiştirin ve *Parola'yı* sertifikanın parolasıyla değiştirin.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Örneğin, bir eklenti, windows form uygulaması veya Windows Presentation Foundation tarayıcı uygulaması için bir uygulama bildirimini imzalamak için aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikalar, üretim ortamlarına dağıtım için önerilmez.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Yer tutucu adlarını önceki adımdaki gibi değiştirerek dağıtım bildirimi dosyasını güncelleştirmek ve imzalamak için aşağıdaki komutu yazın.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Örneğin, excel eklentisi, Windows Forms uygulaması veya Windows Presentation Foundation tarayıcı uygulaması için dağıtım bildirimini güncelleştirmek ve imzalamak için aşağıdaki komutu çalıştırabilirsiniz.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. *.deploy* dosya uzantısını uygulama ve dağıtım bildirimi dosyaları dışında dosyalara geri ekleyin.

7. İsteğe bağlı olarak, ana dağıtım bildirimini *(uygulama>.application\\\<yayımla)* sürüm dağıtım dizininize kopyalayın (*yayım\Uygulama Dosyaları\\\<>_\<sürüm>). *

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Nasıl Yapılır: ClickOnce güvenlik ayarlarını etkinleştirin](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapilir: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılsın: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl?](securing-clickonce-applications.md)
- [Nasıl yapIlir: ClickOnce uygulamaları için istemci bilgisayara güvenilir bir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Nasıl yapılandırılır: ClickOnce güven istemi davranışını yapılandırın](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)