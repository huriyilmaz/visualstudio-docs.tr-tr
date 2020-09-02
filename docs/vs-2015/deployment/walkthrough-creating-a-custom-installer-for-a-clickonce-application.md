---
title: 'İzlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebde75fdf36c84f40ae660a24d469c36e72ceaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821332"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>İzlenecek Yol: ClickOnce Uygulaması için Özel bir Yükleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir. exe dosyasını temel alan herhangi bir ClickOnce uygulaması sessizce yüklenebilir ve özel bir yükleyici tarafından güncelleştirilir. Özel bir yükleyici, yükleme sırasında güvenlik ve bakım işlemlerine yönelik özel iletişim kutuları dahil olmak üzere özel kullanıcı deneyimi uygulayabilir. Yükleme işlemlerini gerçekleştirmek için özel yükleyici <xref:System.Deployment.Application.InPlaceHostingManager> sınıfını kullanır. Bu izlenecek yol, bir ClickOnce uygulamasını sessizce yükleyen özel bir yükleyicinin nasıl oluşturulacağını göstermektedir.  
  
## <a name="prerequisites"></a>Ön koşullar  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Özel bir ClickOnce uygulama yükleyicisi oluşturmak için  
  
1. ClickOnce uygulamanızda, System. Deployment ve System. Windows. Forms 'a başvurular ekleyin.  
  
2. Uygulamanıza yeni bir sınıf ekleyin ve herhangi bir ad belirtin. Bu izlenecek yol, adını kullanır `MyInstaller` .  
  
3. Aşağıdaki `Imports` veya `using` deyimlerini Yeni sınıfınızın en üstüne ekleyin.  
  
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
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
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
  
## <a name="next-steps"></a>Sonraki Adımlar  
 ClickOnce uygulaması, güncelleştirme işlemi sırasında gösterilecek özel bir kullanıcı arabirimi de dahil olmak üzere özel güncelleştirme mantığı da ekleyebilir. Daha fazla bilgi için bkz. <xref:System.Deployment.Application.UpdateCheckInfo>. ClickOnce uygulaması ayrıca bir öğesi kullanarak standart Başlat menüsü girdisi, kısayol ve Program Ekle veya Kaldır girişini de engelleyebilir `<customUX>` . Daha fazla bilgi için bkz. [ \<entryPoint> öğesi](../deployment/entrypoint-element-clickonce-application.md) ve <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint> Dosyalarında](../deployment/entrypoint-element-clickonce-application.md)
