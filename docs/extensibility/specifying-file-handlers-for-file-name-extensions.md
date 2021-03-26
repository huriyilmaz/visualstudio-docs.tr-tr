---
title: Dosya adı uzantıları için dosya Işleyicileri belirtme | Microsoft Docs
description: OpenWithList ve Openwithprogıds kullanarak Visual Studio SDK 'da hangi uygulamanın bir dosya uzantısını işlediğini nasıl belirleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65705467b1531e139c0ec857d6a7b57015d5f2f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089972"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme
Belirli bir dosya uzantısına sahip olan bir dosyayı işleyen uygulamayı belirlemenin çeşitli yolları vardır. OpenWithList ve Openwithprogıd fiilleri, dosya uzantısının kayıt defteri girişi altında dosya işleyicilerini belirtmek için iki yol sunar.

## <a name="openwithlist-verb"></a>OpenWithList fiili
 Windows Gezgini 'nde bir dosyaya sağ tıkladığınızda, **Aç** komutunu görürsünüz. Birden fazla ürün bir uzantıyla ilişkiliyse, **birlikte Aç** alt menüsünü görürsünüz.

 HKEY_CLASSES_ROOT dosya uzantısı için OpenWithList anahtarını ayarlayarak bir uzantıyı açmak üzere farklı uygulamalar kaydedebilirsiniz. Bir dosya uzantısı için bu anahtar altında listelenen uygulamalar, **birlikte Aç** Iletişim kutusunda **Önerilen programlar** başlığının altında görüntülenir. Aşağıdaki örnek,. VCPROJ dosya uzantısını açmak için kaydedilen uygulamaları gösterir.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Uygulamaları belirten anahtarlar HKEY_CLASSES_ROOT\Applications altındaki listeden alınır.

 Bir OpenWithList anahtarı ekleyerek, başka bir uygulama uzantının sahipliğini alıp alsa bile uygulamanızın bir dosya uzantısını desteklediğini bildirirsiniz. Bu, uygulamanızın veya başka bir uygulamanın gelecek bir sürümü olabilir.

## <a name="openwithprogids"></a>Openwithprogıds
 Programlı tanımlayıcılar (ProgID 'ler), bir uygulamanın veya COM nesnesinin bir sürümünü tanımlayan, ClassID 'lerin kolay sürümleridir. Tüm ortak creatable nesneleri kendi program adına sahip olmalıdır. Örneğin, VisualStudio. DTE. 7.1, VisualStudio. DTE. 10.0 başladığında Visual Studio .NET 2003 'yi başlatır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Proje türü veya proje öğesi türü sahibi olarak, dosya uzantınız için sürüme özgü bir ProgID oluşturmanız gerekir. Bu Progıd 'ler, birden fazla ProgID 'nin aynı uygulamayı başlatabileceğinden gereksiz olabilir. Daha fazla bilgi için bkz. [dosya adı uzantıları Için fiiller kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md).

 Diğer satıcıların kaydıyla tekrardan kaçınmak için sürümlenmiş dosya ProgID 'leri için aşağıdaki adlandırma kuralını kullanın:

|Dosya uzantısı|Sürümlü program kimliği|
|--------------------|----------------------|
|. Extension|ProductName. . VersionAna. versionMinor uzantısı|

 Sürümlü ProgID 'leri HKEY_CLASSES_ROOT \\ \Openwithprogıds anahtarına değer olarak ekleyerek belirli bir dosya uzantısını açabiliyor olan farklı uygulamaları kaydedebilirsiniz *\<extension>* . Bu kayıt defteri anahtarı, dosya uzantısıyla ilişkili alternatif ProgID listesini içerir. Listelenen ProgID 'ler ile ilişkili uygulamalar,_ürün adı_ **ile aç** alt menüsünde görüntülenir. Aynı uygulama hem hem de `OpenWithList` `OpenWithProgids` anahtarında belirtilmişse, işletim sistemi yinelenenleri birleştirir.

> [!NOTE]
> `OpenWithProgids`Anahtar yalnızca WINDOWS XP 'de desteklenir. Diğer işletim sistemleri bu anahtarı yoksaydığı için dosya işleyicileri için tek kayıt olarak kullanmayın. Windows XP 'de daha iyi bir kullanıcı deneyimi sağlamak için bu anahtarı kullanın.

 İstenen ProgID 'leri REG_NONE türü değerler olarak ekleyin. Aşağıdaki kod, bir dosya uzantısı için ProgID 'leri kaydetme örneği sağlar (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Dosya uzantısı için varsayılan değer olarak belirtilen ProgID varsayılan dosya işleyicisidir. ' Nin önceki bir sürümü ile birlikte gelen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya diğer uygulamalar tarafından alınabilecek bir dosya uzantısı Için ProgID 'yi değiştirirseniz, `OpenWithProgids` Dosya uzantınızın anahtarını kaydetmeniz ve yeni ProgID 'yi, destekettiğiniz eski ProgID 'ler ile birlikte belirtmeniz gerekir. Örnek:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Eski ProgID ile ilişkili fiiller varsa, bu fiiller kısayol menüsündeki *ürün adıyla* **Aç** altında da görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Dosya Adı Uzantıları Hakkında](../extensibility/about-file-name-extensions.md)
- [Dosya Adı Uzantıları için Fiil Kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)
