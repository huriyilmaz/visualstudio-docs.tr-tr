---
title: vsıx Project şablonu | Microsoft Docs
description: vsıx projesindeki Visual Studio uzantıları kaydırmak için vsıx Project şablonunu nasıl kullanacağınızı öğrenin ve ardından paketi Visual Studio market 'te yayımlayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 781ee248999510bf28323d34e6fe8025bd40f9c317656045b3c196f15499d029
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335231"
---
# <a name="vsix-project-template"></a>VSıX proje şablonu

vsıx projesindeki bir veya daha fazla Visual Studio uzantısını kaydırmak için vsıx Project şablonunu kullanabilir ve sonra paketi [Visual Studio market](https://marketplace.visualstudio.com/) Web sitesinde yayımlayabilirsiniz.

 VSıX dağıtımı VSPackages, derlemeler, MEF Bileşenleri, proje şablonları, öğe şablonları, araç kutusu denetimleri ve özel uzantı türlerini destekler.

> [!NOTE]
> vsıx projelerini kullanmak için Visual Studio SDK 'sını yüklemelisiniz. Visual Studio sdk hakkında daha fazla bilgi için bkz. [Visual Studio sdk](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>VSıX proje şablonunun nerede bulunacağı

vsıx Project şablonu, **yeni Project** iletişim kutusunda "vsıx" araması yaparak kullanılabilir.  hem C# hem de Visual Basic sürümü vardır.

> [!TIP]
> **yeni Project** iletişim kutusunun üst kısmındaki aşağı açılan liste kutusunda .NET Framework 4,5 veya üzeri bir sürümü belirtildiğinden emin olmanız gerekir.

## <a name="uses-of-the-vsix-project-template"></a>VSıX proje şablonunun kullanımları

VSıX proje şablonunun iki ana kullanımı vardır:

- Proje şablonları, öğe şablonları ve uzantıları dağıtmak için.

- Birden çok uzantı çıkışını tek bir dağıtım paketine kaydırmak için.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Boş bir VSıX projesinde uzantı paketleme

Mevcut bir uzantıyı veya VSıX desteği olmayan bir uzantıyı boş bir VSıX projesinde sarmalayarak paketleyebilir. Sarmalanacak uzantı [VSIX şeması](../extensibility/vsix-extension-schema-2-0-reference.md)tarafından desteklenen bir türde olmalıdır.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSıX projesi kullanarak bir uzantıyı paketlemek için

1. Uzantınızı oluşturan projeleri oluşturun.

2. **vsıx Project** şablonunu kullanarak bir vsıx projesi oluşturun.

    *Source. Extension. valtmanifest* , **bildirim tasarımcısında** açılır.

3. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

    **Yeni varlık Ekle** iletişim kutusu görüntülenir.

4. **Tür** listesinde, eklenecek uzantı türünü seçin.

5. Geçerli çözüme (örneğin, bir öğe şablonu veya derlenmiş derleme) dahil olan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları uygulayın:

   1. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

   2. **Project** listesinde, uzantının adını seçin.

   3. **Bu klasöre Ekle** kutusuna varlığın ekleneceği bir klasörün adını girin ve **Tamam** düğmesini seçin.

6. Geçerli çözüme dahil olmayan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları uygulayın:

   1. **Kaynak** liste kutusunda **dosya sistemi üzerinde dosya**' yı seçin.

   2. **Yol** alanına, derlenen veya sıkıştırılan uzantı dosyasının tam yolunu girin veya dosyaya gitmek için **Araştır** düğmesini kullanın.

   3. **Bu klasöre Ekle** kutusuna varlığın ekleneceği bir klasörün adını girin ve **Tamam** düğmesini seçin.

7. Paketinizin ek uzantılar içermesini istiyorsanız, bunları aynı şekilde ekleyin.

8. Çözümü derleyin.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSıX bildirim dosyası, bir [Content_Types]*.xml* dosyası ve projeye eklediğiniz tüm uzantı varlıklarını içeren bir *. vsix* dosyası oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [VSıX uzantı Şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
