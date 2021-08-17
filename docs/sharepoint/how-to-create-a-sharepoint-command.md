---
title: 'nasıl yapılır: SharePoint komutu oluşturma | Microsoft Docs'
description: bir SharePoint araçları uzantısında sunucu nesne modelinin apı 'sini çağırmak için özel bir SharePoint komutu oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7973cd0c3a52ae4433c85b9b0fa71cecc085827c4d33d542232229b7034d9f63
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121228694"
---
# <a name="how-to-create-a-sharepoint-command"></a>nasıl yapılır: SharePoint komutu oluşturma
  sunucu nesne modelini bir SharePoint araçları uzantısında kullanmak istiyorsanız, apı 'yi çağırmak için özel bir *SharePoint komutu* oluşturmanız gerekir. sunucu nesne modeline doğrudan çağırasağlayan bir derlemede SharePoint komutunu tanımlarsınız.

 SharePoint komutlarının amacı hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>SharePoint komutu oluşturmak için

1. Aşağıdaki yapılandırmaya sahip bir sınıf kitaplığı projesi oluşturun:

    - 3,5 .NET Framework hedefler. Hedef Framework 'ü seçme hakkında daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

    - AnyCPU veya x64 platformunu hedefler. Varsayılan olarak, sınıf kitaplığı projeleri için hedef platform AnyCPU olur. Hedef platformu seçme hakkında daha fazla bilgi için bkz. [nasıl yapılır: projeleri hedef platformları Için yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > SharePoint araçları uzantısı tanımlayan aynı projede SharePoint komutu uygulayamaz, çünkü SharePoint komutlar .NET Framework 3,5 ve SharePoint araçları uzantıları hedefleyin [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . uzantınız tarafından ayrı bir projede kullanılan SharePoint komutları tanımlamanız gerekir. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint. Komut

    - MICROSOFT. SharePoint

3. projedeki bir sınıfta, SharePoint komutunu tanımlayan bir yöntem oluşturun. Yöntemi aşağıdaki yönergelere uygun olmalıdır:

    - Bir veya iki parametreye sahip olabilir.

         İlk parametre bir <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> nesne olmalıdır. Bu nesne Microsoft sağlar. SharePoint. SPSite veya Microsoft. SharePoint. Komutun yürütüldüğü SPWeb. Ayrıca <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> , **Çıkış** penceresine ileti yazmak için kullanılabilecek bir nesne veya Visual Studio **hata listesi** penceresi de sağlar.

         İkinci parametre tercih ettiğiniz bir tür olabilir, ancak bu parametre isteğe bağlıdır. SharePoint araçları uzantıınızdan veriye veri geçirmeniz gerekiyorsa, bu parametreyi SharePoint komutunuz olarak ekleyebilirsiniz.

    - Dönüş değeri olabilir, ancak bu isteğe bağlıdır.

    - ikinci parametre ve dönüş değeri Windows Communication Foundation (WCF) tarafından seri hale getirilebilen bir tür olmalıdır. Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) ve [XmlSerializer sınıfı kullanılıyor](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Yöntemi herhangi bir görünürlüğe (**genel**, **iç** veya **özel**) sahip olabilir ve statik veya statik olmayan bir işlem olabilir.

4. Yöntemine uygulayın <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> . Bu öznitelik, komut için benzersiz bir tanımlayıcı belirtir; Bu tanımlayıcının yöntem adıyla eşleşmesi gerekmez.

     SharePoint araçları uzantıınızdan komutu çağırdığınızda aynı benzersiz tanımlayıcıyı belirtmeniz gerekir. daha fazla bilgi için bkz. [nasıl yapılır: yürütme SharePoint komutu](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Örnek
 aşağıdaki kod örneğinde tanımlayıcı içeren bir SharePoint komutu gösterilmektedir `Contoso.Commands.UpgradeSolution` . Bu komut, dağıtılan bir çözüme yükseltmek için sunucu nesne modelindeki API 'Leri kullanır.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet5":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet5":::

 örtük ilk parametreye ek olarak <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> , bu komutun ayrıca SharePoint sitesine yükseltilmekte olan. wsp dosyasının tam yolunu içeren özel bir dize parametresi de vardır. daha büyük bir örnek bağlamında bu kodu görmek için bkz. [izlenecek yol: SharePoint projeler için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Kod derleme
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint. Komut

- MICROSOFT. SharePoint

## <a name="deploying-the-command"></a>Komutu dağıtma
 Komutu dağıtmak için, komutu [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanan uzantı derlemesi ile aynı uzantı (*VSIX*) paketine komut derlemesini ekleyin. Ayrıca, Extension. valtmanifest dosyasındaki komut derlemesi için bir giriş de eklemeniz gerekir. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
