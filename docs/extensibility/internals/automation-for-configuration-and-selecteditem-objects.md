---
title: Yapılandırma ve Selecteditıtem nesneleri için Otomasyon | Microsoft Docs
description: Shell ınterop içindeki Configuration ve selecteditem nesnelerini kullanarak Visual Studio derlemeyi ve seçili öğe işlemlerini otomatikleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6764e074bf061f3b6426e2b1577bb5b16c85043e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095055"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Yapılandırma ve Selecteditıtem nesneleri için Otomasyon

Visual Studio yapı ve seçili öğe işlemlerini otomatik hale getirebilirsiniz.

## <a name="automation-for-builds"></a>Derlemeler için Otomasyon

Derleme veya yapılandırmanın, uyguladığınızda sağlanmış bir otomasyon modeli vardır <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md).

Bir VSPackage oluşturup yapılandırma seçeneklerini denetlemek istiyorsanız otomasyon modelini kullanmanız gerekir.

## <a name="automation-for-selecteditem"></a>Selecteditıtem Otomasyonu

`SelectedItem`Visual Studio bir standart uygulama içerdiğinden nesne için bir uygulama sağlamanız gerekmez. Ancak, `SelectedItem` isterseniz nesneyi uygulayabilirsiniz. Arabirimini içeren bir nesne uygulamanız `SelectedItem` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` __VSHPROPID olarak ayarlanan yönteme bir çağrıya yanıt döndürmelidir [. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Otomasyon modeline katkıda bulunma](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
