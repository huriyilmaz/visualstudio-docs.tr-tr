---
title: VSıX proje şablonu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697929"
---
# <a name="vsix-project-template"></a>VSıX proje şablonu

VSIX projesinde bir veya daha fazla Visual Studio uzantısını kaydırmak için VSıX proje şablonunu kullanabilir ve sonra paketi [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesinde yayımlayabilirsiniz.

 VSıX dağıtımı VSPackages, derlemeler, MEF Bileşenleri, proje şablonları, öğe şablonları, araç kutusu denetimleri ve özel uzantı türlerini destekler.

> [!NOTE]
> VSıX projelerini kullanmak için Visual Studio SDK 'sını yüklemelisiniz. Visual Studio SDK hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>VSıX proje şablonunun nerede bulunacağı

VSıX proje şablonu, "VSIX" araması yaparak **Yeni proje** iletişim kutusunda kullanılabilir.  Hem C# hem de Visual Basic sürümü vardır.

> [!TIP]
> **Yeni proje** iletişim kutusunun üst kısmındaki aşağı açılan liste kutusunda .NET Framework 4,5 veya üzeri bir sürümü belirtildiğinden emin olun.

## <a name="uses-of-the-vsix-project-template"></a>VSıX proje şablonunun kullanımları

VSıX proje şablonunun iki ana kullanımı vardır:

- Proje şablonları, öğe şablonları ve uzantıları dağıtmak için.

- Birden çok uzantı çıkışını tek bir dağıtım paketine kaydırmak için.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Boş bir VSıX projesinde uzantı paketleme

Mevcut bir uzantıyı veya VSıX desteği olmayan bir uzantıyı boş bir VSıX projesinde sarmalayarak paketleyebilir. Sarmalanacak uzantı [VSIX şeması](../extensibility/vsix-extension-schema-2-0-reference.md)tarafından desteklenen bir türde olmalıdır.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSıX projesi kullanarak bir uzantıyı paketlemek için

1. Uzantınızı oluşturan projeleri oluşturun.

2. **VSIX proje** şablonunu kullanarak bir VSIX projesi oluşturun.

    *Source. Extension. valtmanifest* , **bildirim tasarımcısında**açılır.

3. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

    **Yeni varlık Ekle** iletişim kutusu görüntülenir.

4. **Tür** listesinde, eklenecek uzantı türünü seçin.

5. Geçerli çözüme (örneğin, bir öğe şablonu veya derlenmiş derleme) dahil olan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları uygulayın:

   1. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

   2. **Proje** listesinde, uzantının adını seçin.

   3. **Bu klasöre Ekle** kutusuna varlığın ekleneceği bir klasörün adını girin ve **Tamam** düğmesini seçin.

6. Geçerli çözüme dahil olmayan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları uygulayın:

   1. **Kaynak** liste kutusunda **dosya sistemi üzerinde dosya**' yı seçin.

   2. **Yol** alanına, derlenen veya sıkıştırılan uzantı dosyasının tam yolunu girin veya dosyaya gitmek için **Araştır** düğmesini kullanın.

   3. **Bu klasöre Ekle** kutusuna varlığın ekleneceği bir klasörün adını girin ve **Tamam** düğmesini seçin.

7. Paketinizin ek uzantılar içermesini istiyorsanız, bunları aynı şekilde ekleyin.

8. Çözümü derleyin.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSıX bildirim dosyası, bir [Content_Types]*. xml* dosyası ve projeye eklediğiniz tüm uzantı varlıklarını içeren bir *. vsix* dosyası oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [VSıX uzantı Şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
