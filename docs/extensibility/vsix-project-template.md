---
title: VSIX Project Şablon | Microsoft Docs
description: VSIX projesinde Visual Studio sarmak için VSIX Project şablonunu kullanmayı ve ardından paketi Visual Studio Market'te yayımlamayı öğrenin.
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
ms.openlocfilehash: 6d6cb7112d404b0ecc9decbc7e5b7caea251ab35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109779"
---
# <a name="vsix-project-template"></a>VSIX proje şablonu

VSIX Project şablonunu kullanarak vsIX projesinde bir veya daha fazla Visual Studio uzantısını sarmalayın ve ardından paketi Visual Studio [Market](https://marketplace.visualstudio.com/) Web sitesinde yayımlayın.

 VSIX dağıtımı VSPackage'ları, derlemeleri, MEF bileşenlerini, proje şablonlarını, öğe şablonlarını, araç kutusu denetimlerini ve özel uzantı türlerini destekler.

> [!NOTE]
> VSIX projelerini kullanmak için Visual Studio SDK'sı yüklemeniz gerekir. Visual Studio SDK hakkında daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="where-to-find-the-vsix-project-template"></a>VSIX proje şablonunu nerede bulamıyorum?

VSIX Project şablonu Yeni Project iletişim  kutusunda "vsix" ifadesini arayarak kullanılabilir.  Hem C# hem de Visual Basic vardır.

> [!TIP]
> Yeni dosya iletişim kutusunun .NET Framework açılan liste kutusunda 4.5 veya daha yüksek bir değer **belirttiğinizden emin Project** gerekir.

## <a name="uses-of-the-vsix-project-template"></a>VSIX proje şablonunun kullanımları

VSIX proje şablonunun iki ana kullanımı vardır:

- Proje şablonlarını, öğe şablonlarını ve uzantıları dağıtmak için.

- Birden çok uzantının çıkışlarını tek bir dağıtım paketine sarmak için.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Boş bir VSIX projesinde bir uzantıyı paketleme

Var olan bir uzantıyı veya ZATEN VSIX desteğine sahip olan bir uzantıyı boş bir VSIX projesine sarmalamanız gerekir. Sarmalandır için uzantı VSIX şeması tarafından desteklenen bir [tür olmalıdır.](../extensibility/vsix-extension-schema-2-0-reference.md)

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX projesi kullanarak bir uzantıyı pakete dahil etmek için

1. Uzantınızı oluşturmak için projeleri derleme.

2. VSIX projesini kullanarak **VSIX projesini Project** oluşturun.

    *Source.extension.vsixmanifest* Bildirim **Tasarımcısı'nda açılır.**

3. Varlıklar **sekmesinde** Yeni **düğmesini** seçin.

    Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

4. Tür **listesinde,** eklemek istediğiniz uzantı türünü seçin.

5. Geçerli çözüme (örneğin, bir öğe şablonu veya derlenmiş derleme) dahil edilen bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları gerçekleştirin:

   1. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

   2. Project **listesinde** uzantının adını seçin.

   3. Bu **klasöre ekle** kutusuna varlığın katıştırılmak istediğiniz klasörün adını girin ve ardından Tamam **düğmesini** seçin.

6. Geçerli çözüme dahil olmayan bir uzantı veya içerik öğesi eklemek için aşağıdaki adımları gerçekleştirin:

   1. Kaynak listesi **kutusunda** Dosya dosya **sisteminde'yi seçin.**

   2. Yol **alanına** derlenmiş veya sıkıştırılmış uzantı dosyasının tam yolunu girin  veya Gözat düğmesini kullanarak dosyaya göz atabilirsiniz.

   3. Bu **klasöre ekle** kutusuna varlığın katıştırılmak istediğiniz klasörün adını girin ve ardından Tamam **düğmesini** seçin.

7. Paketinizin ek uzantılar içermesi için aynı şekilde ekleyin.

8. Çözümü derleyin.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], bir VSIX bildirim dosyası, [Content_Types].xmldosyası ve ** projeye eklenen tüm uzantı varlıklarını içeren *bir .vsix* dosyası derleme.

## <a name="see-also"></a>Ayrıca bkz.

- [VSIX uzantı şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
