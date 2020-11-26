---
title: Yapılandırma ve Selecteditıtem nesneleri için Otomasyon | Microsoft Docs
description: Visual Studio derlemesini ve seçili öğe işlemlerini, Shell Interop içindeki Configuration ve SelectedItem nesnelerini kullanarak otomatikleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bc4b23662efe688146a7266d1b061d2d9611a45
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190076"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Yapılandırma ve Selecteditıtem nesneleri için Otomasyon

Visual Studio 'da derleme ve seçili öğe işlemlerini otomatikleştirebilir.

## <a name="automation-for-builds"></a>Derlemeler için Otomasyon

Derleme veya yapılandırmanın, uyguladığınızda sağlanmış bir otomasyon modeli vardır <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md).

Bir VSPackage oluşturup yapılandırma seçeneklerini denetlemek istiyorsanız otomasyon modelini kullanmanız gerekir.

## <a name="automation-for-selecteditem"></a>Selecteditıtem Otomasyonu

`SelectedItem`Visual Studio standart bir uygulama içerdiğinden nesne için bir uygulama sağlamanız gerekmez. Ancak, `SelectedItem` isterseniz nesneyi uygulayabilirsiniz. Arabirimini içeren bir nesne uygulamanız `SelectedItem` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` __VSHPROPID olarak ayarlanan yönteme bir çağrıya yanıt döndürmelidir [. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Otomasyon modeline katkıda bulunma](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
