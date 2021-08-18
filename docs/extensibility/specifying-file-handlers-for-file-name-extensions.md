---
title: Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme | Microsoft Docs
description: OpenWithList ve OpenWithProgids kullanarak hangi uygulamanın Visual Studio SDK'sı içinde dosya uzantısını işleyeni belirlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 752d34734537d46681a3a5a116640c24adaffb41
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137580"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme
Belirli bir dosya uzantısına sahip bir dosyayı ele alan uygulamayı belirlemenin birkaç yolu vardır. OpenWithList ve OpenWithProgids fiilleri, dosya uzantısı için kayıt defteri girdisi altında dosya işleyicileri belirtmenin iki yolu vardır.

## <a name="openwithlist-verb"></a>OpenWithList Fiili
 Windows Explorer'da bir dosyaya sağ tıklarsanız Aç **komutunu** görüyorsunuz. Bir uzantıyla ilişkili birden fazla ürün varsa, Birlikte Aç **alt** menüsüyle açılır.

 Dosya uzantısı için OpenWithList anahtarını ayarerek uzantıyı açmak için farklı uygulamaları HKEY_CLASSES_ROOT. Bir dosya uzantısı için bu anahtarın altında listelenen uygulamalar, Birlikte Aç iletişim **kutusundaki** Önerilen Programlar **başlığı altında** görünür. Aşağıdaki örnek, .vcproj dosya uzantısını açmak için kaydedilen uygulamaları gösterir.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Uygulamaları belirten anahtarlar, uygulama adı altındaki HKEY_CLASSES_ROOT\Applications.

 OpenWithList anahtarı ekleyerek, başka bir uygulama uzantının sahipliğini alıyor olsa bile uygulamanın bir dosya uzantısını desteklediğini belirtirsiniz. Bu, uygulamanın gelecekteki bir sürümü veya başka bir uygulama olabilir.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Programlı tanımlayıcılar (ProgIDs), bir uygulamanın veya COM nesnesinin bir sürümünü tanımlayan ClassID'lerinin kolay sürümleridir. Ortak olarak creatable her nesnenin kendi ProgID'si olması gerekir. Örneğin, VisualStudio.DTE.7.1 .NET 2003'Visual Studio başlarken, VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] başlatılır. Proje türünün veya proje öğesi türünün sahibi olarak, dosya uzantınız için sürüme özgü bir ProgID oluşturmanız gerekir. Bu ProgID'ler, birden fazla ProgID'nin aynı uygulamayı başlatan bir içinde yedekli olabilir. Daha fazla bilgi için [bkz. Dosya Adı Uzantıları için Fiilleri Kaydetme.](../extensibility/registering-verbs-for-file-name-extensions.md)

 Diğer satıcıların kaydıyla çoğaltılmasından kaçınmak için, sürüme alınan dosya ProgID'leri için aşağıdaki adlandırma kuralını kullanın:

|Dosya uzantısı|Sürüme Sahip ProgID|
|--------------------|----------------------|
|.extension|Productname. extension.versionMajor.versionMinor|

 \OpenWithProgids anahtarına değer olarak sürüme sahip ProgID'ler ekleyerek belirli bir dosya uzantısını açabilecek HKEY_CLASSES_ROOT \\ *\<extension>* uygulamaları kaydedebilirsiniz. Bu kayıt defteri anahtarı, dosya uzantısıyla ilişkili alternatif ProgID'ler listesini içerir. Listelenen ProgID'lerle ilişkili uygulamalar Ürün Adıyla **Aç**_alt_ listesinde görünür. Aynı uygulama hem hem de anahtarlarında `OpenWithList` `OpenWithProgids` belirtilirse, işletim sistemi yinelemeleri birler.

> [!NOTE]
> Anahtar `OpenWithProgids` yalnızca XP'de Windows. Diğer işletim sistemleri bu anahtarı yoksaymalarını, dosya işleyicileri için tek kayıt olarak kullanmaz. Xp'de daha iyi bir kullanıcı deneyimi sağlamak için Windows kullanın.

 İstenen ProgID'leri, REG_NONE. Aşağıdaki kod, bir dosya uzantısı () için ProgID kaydetme örneği sağlar.*ext ).*

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Dosya uzantısı için varsayılan değer olarak belirtilen ProgID, varsayılan dosya işleyicidir. Önceki bir sürümüyle birlikte gelen veya diğer uygulamalar tarafından ele alınarak bir dosya uzantısı için ProgID'yi değiştirirsanız, dosya uzantınız için anahtarı kaydetmeniz ve listede yeni ProgID'yi, desteklemiş eski [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ProgID'lerle birlikte belirtmeniz `OpenWithProgids` gerekir. Örnek:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Eski ProgID ile ilişkilendirilmiş fiiller varsa, bu fiiller kısayol menüsünde ürün adıyla aç  *altında* da görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Dosya Adı Uzantıları Hakkında](../extensibility/about-file-name-extensions.md)
- [Dosya Adı Uzantıları için Fiil Kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)
