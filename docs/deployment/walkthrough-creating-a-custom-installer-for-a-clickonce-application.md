---
title: Uygulama için özel ClickOnce oluşturma
description: Özel bir yükleyicinin bir ClickOnce dosyasını temel alarak sessiz .exe öğrenin.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4d19a93710b2134f7c4878faf8143209bff4e357
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725377"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Adım adım kılavuz: Bir uygulama için özel ClickOnce oluşturma
Bir ClickOnce dosyasını temel alan tüm *.exe* özel bir yükleyici tarafından sessizce yükleniyor ve güncelleştirilebilir. Özel bir yükleyici, güvenlik ve bakım işlemleri için özel iletişim kutuları dahil olmak üzere yükleme sırasında özel kullanıcı deneyimi gerçekleştirebilirsiniz. Yükleme işlemlerini gerçekleştirmek için özel yükleyici sınıfını <xref:System.Deployment.Application.InPlaceHostingManager> kullanır. Bu kılavuzda, bir uygulamanın sessizce yük devredilen özel bir yükleyicinin ClickOnce göstereceğiz.

## <a name="prerequisites"></a>Önkoşullar

### <a name="to-create-a-custom-clickonce-application-installer"></a>Özel bir uygulama ClickOnce oluşturmak için

1. Uygulama ClickOnce System.Deployment ve System'e başvurular ekleyin. Windows. Forms.

2. Uygulamanıza yeni bir sınıf ekleyin ve herhangi bir ad belirtin. Bu kılavuzda adı `MyInstaller` lanır.

3. Aşağıdaki veya `Imports` `using` yönergelerini yeni sınıfınıza ekleyin.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Aşağıdaki yöntemleri sınıfınıza ekleyin.

     Bu yöntemler, dağıtım bildirimini indirmek, uygun izinleri onaylamak, kullanıcıdan yükleme izni istemek ve ardından uygulamayı ClickOnce <xref:System.Deployment.Application.InPlaceHostingManager> önbelleğine yüklemek için yöntemlere çağrır. Özel bir yükleyici, bir ClickOnce uygulamanın önceden güvenilir olduğunu belirtebilir veya yöntem çağrısına güven kararını <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> erteleyebilir. Bu kod uygulamaya önceden güvenir.

    > [!NOTE]
    > Önceden güvenerek atanan izinler, özel yükleyici kodunun izinlerini aşamaz.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs" id="Snippet1":::

5. Kodunuzdan yükleme yapmak için yöntemini `InstallApplication` çağırabilirsiniz. Örneğin sınıfını olarak adlandırılmışsanız `MyInstaller` aşağıdaki şekilde `InstallApplication` çağrısı yapabilirsiniz.

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
 Bir ClickOnce, güncelleştirme işlemi sırasında göstermek üzere özel bir kullanıcı arabirimi de dahil olmak üzere özel güncelleştirme mantığı da ekleyebilir. Daha fazla bilgi için bkz. <xref:System.Deployment.Application.UpdateCheckInfo>. Bir ClickOnce bir öğe kullanarak standart Başlat menüsü girişi, kısayolu ve Program Ekle veya Kaldır girişlerini de `<customUX>` bastırabilirsiniz. Daha fazla bilgi için bkz. [ \<entryPoint> ve](../deployment/entrypoint-element-clickonce-application.md) <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> öğesi.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> Öğe](../deployment/entrypoint-element-clickonce-application.md)
