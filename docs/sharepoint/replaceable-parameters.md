---
title: Değiştirilebilir Parametreler | Microsoft Docs
description: Gerçek değerleri tasarım zamanında bilinmemektedir ve çözüm öğeleri için proje SharePoint değerleri belirten değiştirilebilir parametreleri (belirteçler) gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload: office
ms.openlocfilehash: 7f7def73b011134a670cc79346d1a4e289d9e67252c9889a01a8599ebd603190
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367503"
---
# <a name="replaceable-parameters"></a>Değiştirilebilir parametreler
  Değiştirilebilir parametreler veya *belirteçler,* proje dosyalarının içinde, gerçek değerleri tasarım zamanında SharePoint çözüm öğeleri için değerler sağlamak için kullanılabilir. Bunlar, işlevinde standart şablon [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belirteçleri ile benzerdir. Daha fazla bilgi için [bkz. Şablon Parametreleri.](../ide/template-parameters.md)

## <a name="token-format"></a>Belirteç biçimi
 Belirteçler dolar işareti ($) karakteriyle başlar ve sona erer. Dağıtımda, bir proje bir SharePoint çözüm paketinde (*.wsp* dosyası) paketleneken kullanılan belirteçler gerçek değerlerle değiştirilir. Örneğin, **$SharePoint belirteci. Package.Name$** değeri "Test SharePoint Package" dizesine çözüm olabilir.

## <a name="token-rules"></a>Belirteç kuralları
 Belirteçler için aşağıdaki kurallar geçerlidir:

- Belirteçler satır içinde herhangi bir yerde belirtilebilir.

- Belirteçler birden çok satıra yayamaz.

- Aynı belirteç aynı satırda ve aynı dosyada birden çok kez belirtilebilir.

- Aynı satırda farklı belirteçler belirtilebilir.

  Bu kurallara uymaz belirteçler yoksayılır ve uyarı veya hatayla sonuçlanmaz.

  Belirteçlerin dize değerlerine göre değiştirilmesi, bildirim dönüştürmeden hemen sonra yapılır. Bu değiştirme, kullanıcının bildirim şablonlarını belirteçlerle düzenlemesini sağlar.

### <a name="token-name-resolution"></a>Belirteç adı çözümlemesi
 Çoğu durumda belirteç, nerede bulunduğuna bakılmaksızın belirli bir değere çözümler. Ancak, belirteç bir paket veya özellikle ilgili ise, belirtecin değeri nerede bulunduğuna bağlıdır. Örneğin, bir özellik Paket A'da ise, belirteç `$SharePoint.Package.Name$` "Paket A" değerine çözümler. Aynı özellik B Paketinde ise , `$SharePoint.Package.Name$` "B Paketi" olarak çözümler.

## <a name="tokens-list"></a>Belirteçler listesi
 Aşağıdaki tabloda kullanılabilir belirteçler liste almaktadır.

|Ad|Açıklama|
|----------|-----------------|
|$SharePoint. Project. FileName$|*NewProj.csproj* gibi içeren proje dosyasının adı.|
|$SharePoint. Project. FileNameWithoutExtension$|Dosya adı uzantısı olmadan içeren proje dosyasının adı. Örneğin, "NewProj".|
|$SharePoint. Project. AssemblyFullName$|Içeren projenin çıkış derlemenin görünen adı (güçlü ad).|
|$SharePoint. Project. AssemblyFileName$|Içeren projenin çıkış derlemesi adı.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension$|Dosya adı uzantısı olmadan, içeren projenin çıkış derlemesi adı.|
|$SharePoint. Project. AssemblyPublicKeyToken$|Içeren projenin çıkış derlemesi ortak anahtar belirteci, dizeye dönüştürülür. ("x2" onaltılık biçimde 16 karakter.)|
|$SharePoint. Package.Name$|İçeren paketin adı.|
|$SharePoint. Package.FileName$|İçeren paketin tanım dosyasının adı.|
|$SharePoint. Package.FileNameWithoutExtension$|İçeren paketin tanım dosyasının adı (uzantı olmadan).|
|$SharePoint. Package.Id$|İçeren SharePoint için kimlik. Bir özellik birden fazla pakette kullanılıyorsa bu değer değişir.|
|$SharePoint. Feature.FileName$|Özellik1.özellik gibi içeren özelliğin tanım *dosyasının adı.*|
|$SharePoint. Feature.FileNameWithoutExtension$|Dosya adı uzantısı olmadan özellik tanımı dosyasının adı.|
|$SharePoint. Feature.DeploymentPath$|Pakette özelliği içeren klasörün adı. Bu belirteç, Özellik Tasarımcısı'nda "Dağıtım Yolu" özelliğine eşit olur. Örnek değer: "Project1_Feature1".|
|$SharePoint. Feature.Id$|İçeren SharePoint özelliğin kimlik numarası. Bu belirteç, tüm özellik düzeyi belirteçlerde olduğu gibi, yalnızca bir özellik aracılığıyla pakete dahil edilen dosyalar tarafından kullanılabilir, bir özellik dışında doğrudan pakete eklenmez.|
|$SharePoint. ProjectItem.Name$|Proje öğesinin adı (dosya adı değil), öğesinden **ISharePointProjectItem.Name.**|
|$SharePoint. Yazın. \<GUID> . AssemblyQualifiedName$|Belirteci ile eşleşen türün derleme [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tam adı. biçimi küçük [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] harflidir ve Guid.ToString("D") biçimine (yani xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) karşılık gelir.|
|$SharePoint. Yazın. \<GUID> . FullName$|Belirteçte GUID ile eşleşen türün tam adı. GUID biçimi küçük harflidir ve Guid.ToString("D") biçimine (yani xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) karşılık gelir.|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Belirteç değiştirme dosya uzantıları listesine uzantı ekleme
 Belirteçler teorik olarak pakete dahil edilen bir SharePoint proje öğesine ait herhangi bir dosya tarafından kullanılabilir, ancak varsayılan olarak belirteçleri yalnızca paket dosyalarında, bildirim dosyalarında ve aşağıdaki uzantılara sahip dosyalarda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] arar:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- Webpart

- DWP

  Bu uzantılar `<TokenReplacementFileExtensions>` Microsoft.VisualStudio.SharePoint.targets dosyasındaki öğesi tarafından tanımlanır \\ ve ...<program dosyaları \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools klasörü.

  Ancak listeye ek dosya uzantıları ekleyebilirsiniz. SharePoint targets dosyasının öğesi öncesinde tanımlanan SharePoint herhangi bir `<TokenReplacementFileExtensions>` PropertyGroup \<Import> öğesine SharePoint ekleyin.

> [!NOTE]
> Belirteç değiştirme bir proje derledikten sonra oluştuğu için , *.cs*, *.vb* veya .resx gibi derlenmiş dosya türleri için dosya uzantıları *eklemeyebilirsiniz.* Belirteçler yalnızca derlenmiş değil dosyalarda değiştirilir.

 Örneğin, dosya adı uzantılarını (*.myextension* ve *.yourextension*) belirteç değiştirme dosya adı uzantıları listesine eklemek için, aşağıdakini bir projeye (*.csproj*) dosyasına eklersiniz:

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 Uzantıyı doğrudan hedefler (*.targets*) dosyasına ekebilirsiniz. Bununla birlikte, uzantıyı eklemek, yalnızca sizin değil, SharePoint tüm projelerde uzantı listesini değiştirmektedir. Bu uzantı, sistemde tek geliştirici sizseniz veya projenizin çoğu bunu gerekli hale getirirse kullanışlı olabilir. Ancak, sisteme özgü olduğundan, bu yaklaşım taşınabilir değildir ve bu nedenle, bunun yerine proje dosyasına herhangi bir uzantı eklemeniz önerilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
