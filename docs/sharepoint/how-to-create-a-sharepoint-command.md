---
title: 'Nasıl SharePoint: SharePoint Komut | Microsoft Docs'
description: SharePoint tools uzantısında sunucu nesne modelinin API'sini çağırmaya SharePoint özel bir SharePoint öğrenin.
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
ms.openlocfilehash: caaca2226b80a1e1aef4246094a01c158b8e2951
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136059"
---
# <a name="how-to-create-a-sharepoint-command"></a>Nasıl SharePoint: SharePoint oluşturma
  Sunucu nesne modelini bir SharePoint araçları uzantısında kullanmak için API'yi SharePoint *özel* bir SharePoint oluşturmanız gerekir. Doğrudan sunucu SharePoint çağıran bir derlemede SharePoint komutunu tanımlarsınız.

 Komut oluşturma komutlarının amacı hakkında daha SharePoint için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

### <a name="to-create-a-sharepoint-command"></a>Bir SharePoint oluşturmak için

1. Aşağıdaki yapılandırmaya sahip bir sınıf kitaplığı projesi oluşturun:

    - 3.5 .NET Framework hedefle. Hedef çerçeveyi seçme hakkında daha fazla bilgi için [bkz. Nasıl 2011:](../ide/visual-studio-multi-targeting-overview.md).NET Framework.

    - AnyCPU veya x64 platformunu hedefler. Varsayılan olarak, sınıf kitaplığı projeleri için hedef platform AnyCPU'dur. Hedef platformu seçme hakkında daha fazla bilgi için [bkz. Nasıl yapılandırılır: Projeleri Hedef Platformlara Yapılandırma.](../ide/how-to-configure-projects-to-target-platforms.md)

    > [!NOTE]
    > SharePoint komutları .NET Framework 3.5'i ve SharePoint araçları uzantılarını hedefleyeli olduğundan, SharePoint araçları uzantısını tanımlayan aynı projede bir SharePoint komutu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] uygulayamazsınız. Uzantınız tarafından kullanılan SharePoint komutlarını ayrı bir projede tanımlamanız gerekir. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint. Komut

    - Microsoft. SharePoint

3. Projesinde bir sınıfta, SharePoint komutunu tanımlayan bir SharePoint oluşturun. yöntemi aşağıdaki yönergelere uygun olmalıdır:

    - Bir veya iki parametreye sahip olabilir.

         İlk parametre bir nesnesi <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> olmalıdır. Bu nesne Microsoft'u sağlar. SharePoint. SPSite veya Microsoft. SharePoint. Komutun yürütül olduğu SPWeb. Ayrıca, çıkış penceresinde veya hata listesinde hata listesi penceresine ileti yazmak için <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> kullanılan bir Visual Studio.  

         İkinci parametre istediğiniz türde olabilir ancak bu parametre isteğe bağlıdır. Bu parametreyi, SharePoint araçları uzantısından komuta veri SharePoint komutunuz için ekebilirsiniz.

    - Dönüş değerine sahip olabilir, ancak bu isteğe bağlıdır.

    - İkinci parametre ve dönüş değeri, Communication Foundation (WCF) tarafından Windows türü olmalıdır. Daha fazla bilgi için [bkz. Veri Sözleşmesi Seri](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) Hale Getiricisi Tarafından Desteklenen Türler [ve XmlSerializer Sınıfını Kullanma.](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)

    - yöntemi herhangi bir görünürlüğüne **(genel,** **iç** veya **özel)** sahip olabilir ve statik veya statik olmayan olabilir.

4. metoduna <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> uygulama. Bu öznitelik, komutu için benzersiz bir tanımlayıcı belirtir; Bu tanımlayıcının yöntem adıyla eşleşmesi gerek değildir.

     SharePoint tools uzantısından komutunu çağırarak aynı benzersiz SharePoint belirtebilirsiniz. Daha fazla bilgi için, [bkz. How to: Execute a SharePoint .](../sharepoint/how-to-execute-a-sharepoint-command.md)

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, tanımlayıcısına SharePoint bir komut örneği `Contoso.Commands.UpgradeSolution` gösteriyor. Bu komut, dağıtılan bir çözüme yükseltmek için sunucu nesne modelinde API'leri kullanır.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet5":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet5":::

 Bu komut, örtülü ilk parametreye ek olarak, SharePoint sitesine yükseltilen .wsp dosyasının tam yolunu içeren özel bir <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> dize parametresine de sahip olur. Bu kodu daha büyük bir örnek bağlamında görmek için bkz. Adım adım: Proje oluşturmak için [özel SharePoint oluşturma.](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

## <a name="compiling-the-code"></a>Kod derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint. Komut

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Komutu dağıtma
 Komutu dağıtmak için komut derlemesini, komutunu kullanan uzantı derlemesi ile aynı uzantı [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (*vsix*) paketine dahil edin. Extension.vsixmanifest dosyasında komut derlemesi için de bir girdi eklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nesne modellerini SharePoint çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Nasıl: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
