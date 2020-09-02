---
title: Değiştirilebilen parametreler | Microsoft Docs
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
manager: jillfra
ms.workload: office
ms.openlocfilehash: 165ef1256a0150e0942d85c4f876c8b3f5e15c72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825313"
---
# <a name="replaceable-parameters"></a>Değiştirilebilen parametreler
  Değiştirilebilir parametreler veya *belirteçler*, gerçek değerleri tasarım zamanında bilinen SharePoint çözüm öğeleri için değerler sağlamak üzere proje dosyaları içinde kullanılabilir. Bunlar işlev olarak standart [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] şablon belirteçlerine benzerdir. Daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

## <a name="token-format"></a>Belirteç biçimi
 Belirteçler bir dolar işareti ($) karakteriyle başlar ve biter. Dağıtım sırasında, bir proje bir SharePoint çözüm paketine (*. wsp* dosyası) paketlenirken kullanılan tüm belirteçler gerçek değerlerle değiştirilmiştir. Örneğin, **$SharePoint. Package.Name $** belirteci "test SharePoint paketini" dizesine çözümleyebilir.

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
|$SharePoint. Project. FileName $|İçeren proje dosyasının adı, örneğin, *NewProj. csproj*.|
|$SharePoint. Project. FileNameWithoutExtension $|Dosya adı uzantısı olmayan kapsayan proje dosyasının adı. Örneğin, "NewProj".|
|$SharePoint. Project. AssemblyFullName $|İçerilen projenin çıkış derlemesinin görünen adı (tanımlayıcı ad).|
|$SharePoint. Project. AssemblyFileName $|İçerilen projenin çıkış derlemesinin adı.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|Dosya adı uzantısı olmadan, kapsayan projenin çıkış derlemesinin adı.|
|$SharePoint. Project. AssemblyPublicKeyToken $|İçerilen projenin çıkış derlemesinin ortak anahtar belirteci bir dizeye dönüştürüldü. ("X2" onaltılık biçiminde 16 karakter.)|
|$SharePoint. Package.Name $|Kapsayan paketin adı.|
|$SharePoint. Package. FileName $|Kapsayan paketin tanım dosyasının adı.|
|$SharePoint. Package. FileNameWithoutExtension $|Kapsayan paketin tanım dosyasının adı (uzantısı olmadan).|
|$SharePoint. Package.Id $|Kapsayan paket için SharePoint KIMLIĞI. Bir özellik birden fazla pakette kullanılıyorsa, bu değer değişecektir.|
|$SharePoint. Feature. FileName $|*Özellik1. feature*gibi kapsayan özelliğin tanım dosyasının adı.|
|$SharePoint. Feature. FileNameWithoutExtension $|Dosya adı uzantısı olmadan Özellik tanım dosyasının adı.|
|$SharePoint. Feature. DeploymentPath $|Paketteki özelliği içeren klasörün adı. Bu belirteç, özellik tasarımcısında "dağıtım yolu" özelliğine sahiptir. Örnek bir değer, "Project1_Feature1".|
|$SharePoint. Feature.Id $|Kapsayan özelliğin SharePoint KIMLIĞI. Tüm özellik düzeyinde belirteçlerde olduğu gibi, bu belirteç yalnızca bir özellik aracılığıyla bir pakette bulunan dosyalar tarafından, bir özellik dışında doğrudan bir pakete eklenmemiş olan dosyalar tarafından kullanılabilir.|
|$SharePoint. ProjectItem.Name $|**ISharePointProjectItem.Name**öğesinden alınan proje öğesinin adı (dosya adı değil).|
|$SharePoint. Type. \<GUID> . AssemblyQualifiedName $|Belirtecin türüyle eşleşen türün derleme nitelikli adı [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] . Biçimi [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] küçük harfli ve Guid. ToString ("D") biçimine (yani, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) karşılık gelir.|
|$SharePoint. Type. \<GUID> . FullName $|Belirteçteki GUID ile eşleşen türün tam adı. GUID 'nin biçimi küçük harfli ve Guid. ToString ("D") biçimine (yani, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx) karşılık gelir.|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Belirteç değiştirme dosyası uzantıları listesine uzantı ekleme
 Belirteçlerin teorik olarak pakete dahil edilen bir SharePoint proje öğesine ait olan herhangi bir dosya tarafından kullanılmasına karşın, varsayılan olarak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yalnızca paket dosyalarında, bildirim dosyalarında ve aşağıdaki uzantılara sahip dosyalarda belirteçleri arar:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- U

- DWP

  Bu uzantılar, `<TokenReplacementFileExtensions>` ... \\<Program Files \> \Msbuild\microsoft\visualstudio\v11.0\SharePointTools klasöründe bulunan Microsoft. VisualStudio. SharePoint. targets dosyasındaki öğesi tarafından tanımlanır.

  Ancak, listeye ek dosya uzantıları ekleyebilirsiniz. SharePoint `<TokenReplacementFileExtensions>` hedefleri dosyasından önce tanımlanan SharePoint proje dosyasındaki herhangi bir PropertyGroup 'a bir öğe ekleyin \<Import> .

> [!NOTE]
> Bir proje derlendikten sonra belirteç değişikliği gerçekleştiğinden, *. cs*, *. vb* veya *. resx*gibi derlenmiş dosya türleri için dosya uzantıları eklememelisiniz. Belirteçler yalnızca derlenmemiş dosyalarda yer alır.

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

 Uzantıyı doğrudan hedefler (*. targets*) dosyasına ekleyebilirsiniz. Ancak, uzantıyı eklemek yalnızca kendi kendinize değil yerel sisteme paketlenmiş tüm SharePoint projeleri için Uzantılar listesini değiştirir. Bu uzantı, sistemde tek geliştirici olduğunda veya projelerinizin büyük bir kısmını gerektiriyorsa kullanışlı olabilir. Ancak, sisteme özgü olduğundan bu yaklaşım taşınabilir değildir ve bu nedenle, bunun yerine proje dosyasına herhangi bir uzantı eklemeniz önerilir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
