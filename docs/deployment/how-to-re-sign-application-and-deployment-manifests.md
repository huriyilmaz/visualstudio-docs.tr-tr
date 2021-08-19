---
title: Uygulama ve dağıtım bildirimlerini yeniden imzala | Microsoft Docs
description: Dağıtım özelliklerine değişiklikler yapıldıktan sonra uygulama ve dağıtım bildirimlerinin her ikisini de bir sertifikayla yeniden imzalamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 9eccc8cb2e56a227548102d1aa342d9399a489bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080565"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama
uygulama bildiriminde Windows Forms uygulamalar, Windows Presentation Foundation uygulamalar (xbap) veya Office çözümleri için dağıtım özelliklerinde değişiklikler yaptıktan sonra, hem uygulama hem de dağıtım bildirimlerini bir sertifikayla yeniden imzalamanız gerekir. Bu işlem, değiştirilen dosyaların son kullanıcı bilgisayarlarında yüklü olmamasını sağlamaya yardımcı olur.

 Bildirimleri yeniden imzalayabileceğiniz başka bir senaryo ise müşterilerinizin uygulama ve dağıtım bildirimlerini kendi sertifikasıyla imzalamasını ister.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini yeniden imzalama
 Bu yordam, uygulama bildirimi dosyanızda (*. manifest*) daha önce değişiklikler yapmış olduğunuzu varsayar. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım özelliklerini değiştirme](/previous-versions/cc442869(v=vs.110)).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım bildirimlerini Mage.exe ile yeniden imzalamak için

1. bir **Visual Studio komut istemi** penceresi açın.

2. Dizinleri imzalamak istediğiniz bildirim dosyalarını içeren klasör olarak değiştirin.

3. Uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. *Manifestfilename* değerini bildirim dosyanızın adıyla ve uzantısıyla değiştirin. Sertifikayı sertifika dosyasının göreli veya tam *yoluyla değiştirin ve* *parolayı* sertifika parolasıyla değiştirin.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     örneğin, bir eklenti, bir Windows Form uygulaması veya bir Windows Presentation Foundation tarayıcı uygulaması için bir uygulama bildirimini imzalamak üzere aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikaların üretim ortamlarına dağıtılması önerilmez.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Dağıtım bildirimi dosyasını güncelleştirmek ve imzalamak için, önceki adımda olduğu gibi yer tutucu adlarını değiştirerek aşağıdaki komutu yazın.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     örneğin, bir Excel eklentisinin, Windows Forms uygulamasının veya Windows Presentation Foundation tarayıcı uygulamasının bir dağıtım bildirimini güncelleştirmek ve imzalamak için aşağıdaki komutu çalıştırabilirsiniz.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. İsteğe bağlı olarak, ana dağıtım bildirimini (*Publish \\ \<appname> . Application*) sürüm dağıtım dizininize (*publish\Application Files \\ \<appname> _ \<version>*) kopyalayın.

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini güncelleştirin ve yeniden imzalayın
 Bu yordam, uygulama bildirimi dosyanızda (*. manifest*) daha önce değişiklikler yapmış olduğunu, ancak güncelleştirilmiş başka dosyalar olduğunu varsayar. Dosyalar güncelleştirilirken, dosyayı temsil eden karma değeri de güncelleştirilmeleri gerekir.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Uygulama ve dağıtım bildirimlerini Mage.exe ile güncelleştirmek ve yeniden imzalamak için

1. bir **Visual Studio komut istemi** penceresi açın.

2. Dizinleri imzalamak istediğiniz bildirim dosyalarını içeren klasör olarak değiştirin.

3. Yayımla çıkış klasöründeki dosyalardan *. deploy* dosya uzantısını kaldırın.

4. Uygulama bildirimini güncelleştirilmiş dosyalar için yeni karmalarla güncelleştirmek ve uygulama bildirim dosyasını imzalamak için aşağıdaki komutu yazın. *Manifestfilename* değerini bildirim dosyanızın adıyla ve uzantısıyla değiştirin. Sertifikayı sertifika dosyasının göreli veya tam *yoluyla değiştirin ve* *parolayı* sertifika parolasıyla değiştirin.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     örneğin, bir eklenti, bir Windows Form uygulaması veya bir Windows Presentation Foundation tarayıcı uygulaması için bir uygulama bildirimini imzalamak üzere aşağıdaki komutu çalıştırabilirsiniz. Visual Studio tarafından oluşturulan geçici sertifikaların üretim ortamlarına dağıtılması önerilmez.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Dağıtım bildirimi dosyasını güncelleştirmek ve imzalamak için, önceki adımda olduğu gibi yer tutucu adlarını değiştirerek aşağıdaki komutu yazın.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     örneğin, bir Excel eklentisinin, Windows Forms uygulamasının veya Windows Presentation Foundation tarayıcı uygulamasının bir dağıtım bildirimini güncelleştirmek ve imzalamak için aşağıdaki komutu çalıştırabilirsiniz.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Uygulama ve dağıtım bildirim dosyaları dışında *. deploy* dosya uzantısını dosyalara geri ekleyin.

7. İsteğe bağlı olarak, ana dağıtım bildirimini (*Publish \\ \<appname> . Application*) sürüm dağıtım dizininize (*publish\Application Files \\ \<appname> _ \<version>*) kopyalayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)
- [nasıl yapılır: ClickOnce bir uygulama için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [nasıl yapılır: bir ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [nasıl yapılır: kısıtlanmış izinlerle ClickOnce bir uygulamada hata ayıklama](securing-clickonce-applications.md)
- [nasıl yapılır: ClickOnce uygulamalar için bir istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [nasıl yapılır: ClickOnce güven istemi davranışını yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)