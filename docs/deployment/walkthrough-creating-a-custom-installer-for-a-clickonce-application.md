---
title: ClickOnce uygulaması için özel yükleyici oluşturma
description: Özel bir yükleyicinin bir. exe dosyasını temel alan bir ClickOnce uygulamasını sessizce yükleyip güncelleştiremeyeceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 748d9f5932f93261bc991f0d8af43728b8e5ce02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917291"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>İzlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma
Bir *. exe* dosyasını temel alan herhangi bir ClickOnce uygulaması sessizce yüklenebilir ve özel bir yükleyici tarafından güncelleştirilir. Özel bir yükleyici, yükleme sırasında güvenlik ve bakım işlemlerine yönelik özel iletişim kutuları dahil olmak üzere özel kullanıcı deneyimi uygulayabilir. Yükleme işlemlerini gerçekleştirmek için özel yükleyici <xref:System.Deployment.Application.InPlaceHostingManager> sınıfını kullanır. Bu izlenecek yol, bir ClickOnce uygulamasını sessizce yükleyen özel bir yükleyicinin nasıl oluşturulacağını göstermektedir.

## <a name="prerequisites"></a>Önkoşullar

### <a name="to-create-a-custom-clickonce-application-installer"></a>Özel bir ClickOnce uygulama yükleyicisi oluşturmak için

1. ClickOnce uygulamanızda, System. Deployment ve System. Windows. Forms 'a başvurular ekleyin.

2. Uygulamanıza yeni bir sınıf ekleyin ve herhangi bir ad belirtin. Bu izlenecek yol, adını kullanır `MyInstaller` .

3. Aşağıdaki `Imports` veya `using` yönergelerini Yeni sınıfınızın en üstüne ekleyin.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Sınıfınıza aşağıdaki yöntemleri ekleyin.

     Bu yöntemler <xref:System.Deployment.Application.InPlaceHostingManager> dağıtım bildirimini indirme, uygun izinleri onaylama, kullanıcıdan yükleme iznini isteme ve uygulamayı ClickOnce önbelleğine yükleme ve yükleme yöntemlerini çağırır. Özel bir yükleyici, ClickOnce uygulamasının önceden güvenilir olduğunu belirtebilir veya yöntem çağrısına güven kararını erteleyebilirsiniz <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> . Bu kod, uygulamaya önceden güvenir.

    > [!NOTE]
    > Önceden güvenme tarafından atanan izinler, özel yükleyici kodunun izinlerini aşamaz.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Kodunuzda yükleme yapmayı denemek için `InstallApplication` yöntemini çağırın. Örneğin, sınıfınızı adlandırdıysanız `MyInstaller` `InstallApplication` aşağıdaki şekilde çağrı yapabilirsiniz.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Sonraki adımlar
 ClickOnce uygulaması, güncelleştirme işlemi sırasında gösterilecek özel bir kullanıcı arabirimi de dahil olmak üzere özel güncelleştirme mantığı da ekleyebilir. Daha fazla bilgi için bkz. <xref:System.Deployment.Application.UpdateCheckInfo>. ClickOnce uygulaması ayrıca bir öğesi kullanarak standart Başlat menüsü girdisi, kısayol ve Program Ekle veya Kaldır girişini de engelleyebilir `<customUX>` . Daha fazla bilgi için bkz. [ \<entryPoint> öğesi](../deployment/entrypoint-element-clickonce-application.md) ve <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> dosyalarında](../deployment/entrypoint-element-clickonce-application.md)
