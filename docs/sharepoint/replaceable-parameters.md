---
title: Değiştirilebilen parametreler | Microsoft Docs
description: gerçek değerleri tasarım zamanında bilinen SharePoint çözüm öğeleri için proje dosyaları içinde değerler belirten değiştirilebilen parametreleri (belirteçleri) gözden geçirin.
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
ms.openlocfilehash: e36edf6d8482fcb48a6a77695a6631aed1868203
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092949"
---
# <a name="replaceable-parameters"></a>Değiştirilebilen parametreler
  değiştirilebilir parametreler veya *belirteçler*, gerçek değerleri tasarım zamanında bilinen SharePoint çözüm öğeleri için değerler sağlamak üzere proje dosyaları içinde kullanılabilir. Bunlar işlev olarak standart [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] şablon belirteçlerine benzerdir. Daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

## <a name="token-format"></a>Belirteç biçimi
 Belirteçler bir dolar işareti ($) karakteriyle başlar ve biter. dağıtım sırasında, bir proje SharePoint çözüm paketine (*. wsp* dosyası) paketlenirken kullanılan tüm belirteçler gerçek değerlerle birlikte değişir. Örneğin, **$ SharePoint belirteci. Package.Name $** , "Test SharePoint paketi" dizesine çözüm alabilir.

## <a name="token-rules"></a>Belirteç kuralları
 Aşağıdaki kurallar belirteçler için geçerlidir:

- Belirteçler, bir satırda herhangi bir yerde belirtilebilir.

- Belirteçler birden çok satıra yayılamaz.

- Aynı satırda ve aynı dosyada aynı belirteç birden çok kez belirtilebilir.

- Aynı satırda farklı belirteçler belirtilebilir.

  Bu kurallara uymalıdır belirteçleri yok sayılır ve uyarı ya da hata ile sonuçlanmaz.

  Belirteçleri dize değerlerine göre değiştirme, bildirim dönüşümünde hemen sonra yapılır. Bu değişiklik, kullanıcının bildirim şablonlarını belirteçlerle düzenlemesine izin verir.

### <a name="token-name-resolution"></a>Belirteç adı çözümleme
 Çoğu durumda, bir belirteç bulunduğu yere bakılmaksızın belirli bir değere çözümlenir. Ancak, belirteç bir paket veya özellik ile ilişkiliyse, belirtecin değeri bulunduğu yere bağlıdır. Örneğin, bir özellik A paketinde ise, belirteç `$SharePoint.Package.Name$` "a Package" değerine dönüşür. Aynı özellik B paketinde ise, `$SharePoint.Package.Name$` "Paket B" olarak çözümlenir.

## <a name="tokens-list"></a>Belirteç listesi
 Aşağıdaki tabloda kullanılabilir belirteçler listelenmektedir.

|Ad|Açıklama|
|----------|-----------------|
|$ SharePoint. Project. Dosya adı $|İçeren proje dosyasının adı, örneğin, *NewProj. csproj*.|
|$ SharePoint. Project. FileNameWithoutExtension $|Dosya adı uzantısı olmayan kapsayan proje dosyasının adı. Örneğin, "NewProj".|
|$ SharePoint. Project. AssemblyFullName $|İçerilen projenin çıkış derlemesinin görünen adı (tanımlayıcı ad).|
|$ SharePoint. Project. AssemblyFileName $|İçerilen projenin çıkış derlemesinin adı.|
|$ SharePoint. Project. AssemblyFileNameWithoutExtension $|Dosya adı uzantısı olmadan, kapsayan projenin çıkış derlemesinin adı.|
|$ SharePoint. Project. AssemblyPublicKeyToken $|İçerilen projenin çıkış derlemesinin ortak anahtar belirteci bir dizeye dönüştürüldü. ("X2" onaltılık biçiminde 16 karakter.)|
|$ SharePoint. Package.Name $|Kapsayan paketin adı.|
|$ SharePoint. Package. FileName $|Kapsayan paketin tanım dosyasının adı.|
|$ SharePoint. Package. FileNameWithoutExtension $|Kapsayan paketin tanım dosyasının adı (uzantısı olmadan).|
|$ SharePoint. Package.Id $|kapsayan paketin SharePoint kimliği. Bir özellik birden fazla pakette kullanılıyorsa, bu değer değişecektir.|
|$ SharePoint. Feature. FileName $|*Özellik1. feature* gibi kapsayan özelliğin tanım dosyasının adı.|
|$ SharePoint. Feature. FileNameWithoutExtension $|Dosya adı uzantısı olmadan Özellik tanım dosyasının adı.|
|$ SharePoint. Feature. DeploymentPath $|Paketteki özelliği içeren klasörün adı. Bu belirteç, özellik tasarımcısında "dağıtım yolu" özelliğine sahiptir. Örnek bir değer, "Project1_Feature1".|
|$ SharePoint. Feature.Id $|kapsayan özelliğin SharePoint kimliği. Tüm özellik düzeyinde belirteçlerde olduğu gibi, bu belirteç yalnızca bir özellik aracılığıyla bir pakette bulunan dosyalar tarafından, bir özellik dışında doğrudan bir pakete eklenmemiş olan dosyalar tarafından kullanılabilir.|
|$ SharePoint. ProjectItem.Name $|**ISharePointProjectItem.Name** öğesinden alınan proje öğesinin adı (dosya adı değil).|
|$ SharePoint. Yazın. \<GUID> . AssemblyQualifiedName $|Belirtecin türüyle eşleşen türün derleme nitelikli adı [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] . Biçimi [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] küçük harfli ve Guid. ToString ("D") biçimine (yani, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) karşılık gelir.|
|$ SharePoint. Yazın. \<GUID> . FullName $|Belirteçteki GUID ile eşleşen türün tam adı. GUID 'nin biçimi küçük harfli ve Guid. ToString ("D") biçimine (yani, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) karşılık gelir.|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Belirteç değiştirme dosyası uzantıları listesine uzantı ekleme
 belirteçler, pakete dahil olan bir SharePoint proje öğesine ait olan herhangi bir dosya tarafından teorik olarak kullanılabilse de, varsayılan olarak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yalnızca paket dosyalarındaki belirteçleri, bildirim dosyalarını ve aşağıdaki uzantılara sahip dosyaları arar:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- U

- DWP

  bu uzantılar, `<TokenReplacementFileExtensions>` .. \\ . içinde bulunan Microsoft. VisualStudio. SharePoint. targets dosyasında öğesi tarafından tanımlanır. program dosyaları \> \ MSBuild \microsoft\visualstudio\v11.0\sharepointtools klasörü<.

  Ancak, listeye ek dosya uzantıları ekleyebilirsiniz. `<TokenReplacementFileExtensions>`SharePoint targets dosyasından önce tanımlanan SharePoint proje dosyasındaki herhangi bir propertygroup öğesine bir öğe ekleyin \<Import> .

> [!NOTE]
> Bir proje derlendikten sonra belirteç değişikliği gerçekleştiğinden, *. cs*, *. vb* veya *. resx* gibi derlenmiş dosya türleri için dosya uzantıları eklememelisiniz. Belirteçler yalnızca derlenmemiş dosyalarda yer alır.

 Örneğin, dosya adı uzantılarını (*. MyExtension* ve *. yourexgeri*) belirteç değiştirme dosya adı uzantıları listesine eklemek için aşağıdakileri bir proje (*. csproj*) dosyasına ekleyin:

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

 Uzantıyı doğrudan hedefler (*. targets*) dosyasına ekleyebilirsiniz. ancak, uzantıyı eklemek yalnızca kendi kendinize değil yerel sistemde paketlenmiş tüm SharePoint projeler için uzantılar listesini değiştirir. Bu uzantı, sistemde tek geliştirici olduğunda veya projelerinizin büyük bir kısmını gerektiriyorsa kullanışlı olabilir. Ancak, sisteme özgü olduğundan bu yaklaşım taşınabilir değildir ve bu nedenle, bunun yerine proje dosyasına herhangi bir uzantı eklemeniz önerilir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
