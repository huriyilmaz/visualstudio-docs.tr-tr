---
title: Dosya adı uzantıları için dosya Işleyicileri belirtme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbc85a506b51a29f1c4809890eaeeb0dcecc99a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719573"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme
Belirli bir dosya uzantısına sahip olan bir dosyayı işleyen uygulamayı belirlemenin çeşitli yolları vardır. OpenWithList ve Openwithprogıd fiilleri, dosya uzantısının kayıt defteri girişi altında dosya işleyicilerini belirtmek için iki yol sunar.

## <a name="openwithlist-verb"></a>OpenWithList fiili
 Windows Gezgini 'nde bir dosyaya sağ tıkladığınızda, **Aç** komutunu görürsünüz. Birden fazla ürün bir uzantıyla ilişkiliyse, **birlikte Aç** alt menüsünü görürsünüz.

 HKEY_CLASSES_ROOT içindeki dosya uzantısı için OpenWithList anahtarını ayarlayarak bir uzantıyı açmak üzere farklı uygulamalar kaydedebilirsiniz. Bir dosya uzantısı için bu anahtar altında listelenen uygulamalar, **birlikte Aç** Iletişim kutusunda **Önerilen programlar** başlığının altında görüntülenir. Aşağıdaki örnek,. VCPROJ dosya uzantısını açmak için kaydedilen uygulamaları gösterir.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Uygulamaları belirten anahtarlar HKEY_CLASSES_ROOT\Applications. altındaki listeden alınır

 Bir OpenWithList anahtarı ekleyerek, başka bir uygulama uzantının sahipliğini alıp alsa bile uygulamanızın bir dosya uzantısını desteklediğini bildirirsiniz. Bu, uygulamanızın veya başka bir uygulamanın gelecek bir sürümü olabilir.

## <a name="openwithprogids"></a>Openwithprogıds
 Programlı tanımlayıcılar (ProgID 'ler), bir uygulamanın veya COM nesnesinin bir sürümünü tanımlayan, ClassID 'lerin kolay sürümleridir. Tüm ortak creatable nesneleri kendi program adına sahip olmalıdır. Örneğin, VisualStudio. DTE. 7.1, Visual Studio .NET 2003 'yi başlatır. Bu, VisualStudio. DTE. 10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]başlar. Proje türü veya proje öğesi türü sahibi olarak, dosya uzantınız için sürüme özgü bir ProgID oluşturmanız gerekir. Bu Progıd 'ler, birden fazla ProgID 'nin aynı uygulamayı başlatabileceğinden gereksiz olabilir. Daha fazla bilgi için bkz. [dosya adı uzantıları Için fiiller kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md).

 Diğer satıcıların kaydıyla tekrardan kaçınmak için sürümlenmiş dosya ProgID 'leri için aşağıdaki adlandırma kuralını kullanın:

|Dosya Uzantısı|Sürümlü program kimliği|
|--------------------|----------------------|
|. Extension|ProductName. . VersionAna. versionMinor uzantısı|

 Belirli bir dosya uzantısını açmak için, \Openwithprogıds anahtarı > HKEY_CLASSES_ROOT\\ *\<uzantısına*bir değer olarak sürümlü ProgID 'ler ekleyerek bu farklı uygulamaları kaydedebilirsiniz. Bu kayıt defteri anahtarı, dosya uzantısıyla ilişkili alternatif ProgID listesini içerir. Listelenen ProgID 'ler ile ilişkili uygulamalar,_ürün adı_ **ile aç**alt menüsünde görüntülenir. Aynı uygulama hem `OpenWithList` hem de `OpenWithProgids` anahtarlarında belirtilirse, işletim sistemi yinelenenleri birleştirir.

> [!NOTE]
> `OpenWithProgids` anahtarı yalnızca Windows XP 'de desteklenir. Diğer işletim sistemleri bu anahtarı yoksaydığı için dosya işleyicileri için tek kayıt olarak kullanmayın. Windows XP 'de daha iyi bir kullanıcı deneyimi sağlamak için bu anahtarı kullanın.

 İstenen ProgID 'leri REG_NONE türünün değerleri olarak ekleyin. Aşağıdaki kod, bir dosya uzantısı için ProgID 'leri kaydetme örneği sağlar (. *ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Dosya uzantısı için varsayılan değer olarak belirtilen ProgID varsayılan dosya işleyicisidir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] önceki bir sürümüyle birlikte gelen veya diğer uygulamalar tarafından alınabilecek bir dosya uzantısı için ProgID 'yi değiştirirseniz, dosya uzantınızın `OpenWithProgids` anahtarını kaydetmeniz ve listede yeni ProgID 'yi eski ProgID ile birlikte belirtmeniz gerekir destekliyoruz. Örneğin:

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