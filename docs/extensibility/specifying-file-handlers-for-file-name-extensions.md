---
title: Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699749"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme
Belirli bir dosya uzantısı olan bir dosyayı işleyen uygulamayı belirlemenin birkaç yolu vardır. OpenWithList ve OpenWithProgids fiilleri, dosya uzantısı için kayıt defteri girişinin altında dosya işleyicilerini belirtmenin iki yolu vardır.

## <a name="openwithlist-verb"></a>OpenWithList Fiil
 Windows Gezgini'nde bir dosyayı sağ tıklattığınızda **Aç** komutunu görürsünüz. Birden fazla ürün bir uzantıyla ilişkiliyse, bir **Açık** alt menüsü görürsünüz.

 HKEY_CLASSES_ROOT'da dosya uzantısı için OpenWithList anahtarını ayarlayarak bir uzantı açmak için farklı uygulamaları kaydedebilirsiniz. Dosya uzantısı için bu anahtarın altında listelenen uygulamalar, **Ile Aç** iletişim kutusunda **Önerilen Programlar** başlığıaltında görünür. Aşağıdaki örnekte .vcproj dosya uzantısını açmak için kayıtlı uygulamalar gösterilmektedir.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Uygulamaları belirten anahtarlar HKEY_CLASSES_ROOT\Applications altındaki listeden alınır.

 OpenWithList tuşu ekleyerek, başka bir uygulama uzantının sahipliğini kabul etse bile uygulamanızın bir dosya uzantısını desteklediğini beyan emiş olursunuz. Bu, uygulamanızın veya başka bir uygulamanın gelecekteki bir sürümü olabilir.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Programlı tanımlayıcılar (ProgID'ler), bir uygulamanın veya COM nesnesinin sürümünü tanımlayan Sınıfların arkadaş çafedilir sürümleridir. Her eş-creatable nesnenin kendi ProgID olmalıdır. Örneğin VisualStudio.DTE.7.1 Visual Studio .NET 2003'ü, VisualStudio.DTE.10.0 ise başlar. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proje türü veya proje öğesi türünün sahibi olarak, dosya uzantınız için sürüme özgü bir ProgID oluşturmanız gerekir. Bu ProgID'ler, birden fazla ProgID'nin aynı uygulamayı başlatabileceği nden fazla gereksiz olabilir. Daha fazla bilgi için dosya [adı uzantıları için Fiilleri Kaydetme'ye](../extensibility/registering-verbs-for-file-name-extensions.md)bakın.

 Diğer satıcılardan gelen kayıtla yinelemeyi önlemek için sürümlü dosya ProgID'leri için aşağıdaki adlandırma kuralını kullanın:

|Dosya uzantısı|Sürümlü ProgID|
|--------------------|----------------------|
|.uzantı|Productname. extension.versionMajor.versionMinor|

 \OpenWithProgids tuşu>HKEY_CLASSES_ROOT\\*\<uzantısına *değer olarak sürümlü ProgID'ler ekleyerek belirli bir dosya uzantısını açabilen farklı uygulamaları kaydedebilirsiniz. Bu kayıt defteri anahtarı, dosya uzantısı ile ilişkili alternatif ProgID'lerin bir listesini içerir. Listelenen ProgID'lerle ilişkili uygulamalar Ürün **Open With**_Adı_ yla Açık alt menüsünde görünür. Aynı uygulama hem anahtarlarda `OpenWithList` hem `OpenWithProgids` de anahtarlarda belirtilirse, işletim sistemi yinelenenleri birleştirir.

> [!NOTE]
> Anahtar `OpenWithProgids` yalnızca Windows XP'de desteklenir. Diğer işletim sistemleri bu anahtarı yoksaydığından, dosya işleyicileri için tek kayıt olarak kullanmayın. Windows XP'de daha iyi bir kullanıcı deneyimi sağlamak için bu anahtarı kullanın.

 REG_NONE türündeki değerler olarak istenilen ProgID'leri ekleyin. Aşağıdaki kod, bir dosya uzantısı için ProgID'leri kaydetme nin bir örneğini sağlar (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Dosya uzantısı için varsayılan değer olarak belirtilen ProgID varsayılan dosya işleyicisidir. ProgID'yi önceki sürümüyle gönderilen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya diğer uygulamalar tarafından devralınabilecek bir dosya uzantısı için değiştirirseniz, dosya uzantınızın anahtarını `OpenWithProgids` kaydetmeniz ve desteklediğiniz eski ProgID'lerle birlikte listedeki yeni ProgID'yi belirtmeniz gerekir. Örnek:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Eski ProgID'de onunla ilişkili fiiller varsa, bu fiiller kısayol menüsünde *Ürün Adı* **ile Açık'ın** altında da görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Dosya Adı Uzantıları Hakkında](../extensibility/about-file-name-extensions.md)
- [Dosya Adı Uzantıları için Fiil Kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)
