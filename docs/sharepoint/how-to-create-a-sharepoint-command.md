---
title: 'Nasıl yapılır: SharePoint komutu oluşturma | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c07d541dc4f68f33d48e7cb41b6bc3923b2ea52
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189237"
---
# <a name="how-to-create-a-sharepoint-command"></a>Nasıl yapılır: SharePoint komutu oluşturma
  Sunucu nesne modelini bir SharePoint Araçları uzantısında kullanmak istiyorsanız, API 'yi çağırmak için özel bir *SharePoint komutu* oluşturmanız gerekir. SharePoint komutunu, doğrudan sunucu nesne modeline çağırabilirler bir derlemede tanımlarsınız.

 SharePoint komutlarının amacı hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Bir SharePoint komutu oluşturmak için

1. Aşağıdaki yapılandırmaya sahip bir sınıf kitaplığı projesi oluşturun:

    - 3,5 .NET Framework hedefler. Hedef Framework 'ü seçme hakkında daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

    - AnyCPU veya x64 platformunu hedefler. Varsayılan olarak, sınıf kitaplığı projeleri için hedef platform AnyCPU olur. Hedef platformu seçme hakkında daha fazla bilgi için bkz. [nasıl yapılır: projeleri hedef platformları Için yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > SharePoint komutları, .NET Framework 3,5 ' i ve SharePoint Araçları uzantılarını hedef [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]hedef alan bir SharePoint araçları uzantısı tanımlayan aynı projede bir SharePoint komutu uygulayamaz. Uzantınızın tarafından ayrı bir projede kullanılan herhangi bir SharePoint komutunu tanımlamanız gerekir. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint. Commands

    - Microsoft. SharePoint

3. Projedeki bir sınıfta, SharePoint komutunuz tanımlayan bir yöntem oluşturun. Yöntemi aşağıdaki yönergelere uygun olmalıdır:

    - Bir veya iki parametreye sahip olabilir.

         İlk parametre bir <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> nesnesi olmalıdır. Bu nesne, komutun yürütüldüğü Microsoft. SharePoint. SPSite veya Microsoft. SharePoint. SPWeb ' i sağlar. Ayrıca, Visual Studio 'daki **Çıkış** penceresine veya **hata listesi** penceresine ileti yazmak için kullanılabilecek bir <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> nesnesi de sağlar.

         İkinci parametre tercih ettiğiniz bir tür olabilir, ancak bu parametre isteğe bağlıdır. SharePoint araçları uzantıınızdan komuta veri geçirmeniz gerekiyorsa, bu parametreyi SharePoint komutunuz olarak ekleyebilirsiniz.

    - Dönüş değeri olabilir, ancak bu isteğe bağlıdır.

    - İkinci parametre ve dönüş değeri Windows Communication Foundation (WCF) tarafından seri hale getirilebilen bir tür olmalıdır. Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) ve [XmlSerializer sınıfı kullanılıyor](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Yöntemi herhangi bir görünürlüğe (**genel**, **iç**veya **özel**) sahip olabilir ve statik veya statik olmayan bir işlem olabilir.

4. Yöntemine <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> uygulayın. Bu öznitelik, komut için benzersiz bir tanımlayıcı belirtir; Bu tanımlayıcının yöntem adıyla eşleşmesi gerekmez.

     SharePoint araçları uzantıınızdan komutu çağırdığınızda aynı benzersiz tanımlayıcıyı belirtmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `Contoso.Commands.UpgradeSolution`tanımlayıcısına sahip bir SharePoint komutunu gösterir. Bu komut, dağıtılan bir çözüme yükseltmek için sunucu nesne modelindeki API 'Leri kullanır.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Örtük ilk <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresine ek olarak, bu komutun SharePoint sitesine yükseltilmekte olan. wsp dosyasının tam yolunu içeren özel bir dize parametresi de vardır. Bu kodu daha büyük bir örnek bağlamında görmek için bkz. [Izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint. Commands

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Komutu dağıtma
 Komutu dağıtmak için, komutu kullanan uzantı derlemesi ile aynı [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı (*VSIX*) paketine komut derlemesini ekleyin. Ayrıca, Extension. valtmanifest dosyasındaki komut derlemesi için bir giriş de eklemeniz gerekir. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
