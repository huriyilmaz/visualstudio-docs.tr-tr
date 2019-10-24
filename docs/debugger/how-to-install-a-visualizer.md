---
title: 'Nasıl yapılır: Görselleştirici yüklemesi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c9c2fa8a8fb300c3b7eb702ae3efd216e17141a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733102"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
Görselleştirici oluşturduktan sonra, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ' de kullanılabilmesi için Görselleştiriciyi yüklemelisiniz. Görselleştirici yüklenmesi basit bir işlemdir.

> [!NOTE]
> UWP uygulamalarında yalnızca standart metin, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.

### <a name="to-install-a-visualizer"></a>Görselleştirici yüklemek için

1. Derleyecek Görselleştiriciyi içeren DLL 'i bulun.

2. DLL 'yi aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Uzaktan hata ayıklama için yönetilen bir Görselleştirici kullanmak istiyorsanız, uzak bilgisayardaki aynı yola DLL 'yi kopyalayın.

4. Hata ayıklama oturumunu yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Nasıl Yapılır: Görselleştirici Yazma](/visualstudio/debugger/create-custom-visualizers-of-data)