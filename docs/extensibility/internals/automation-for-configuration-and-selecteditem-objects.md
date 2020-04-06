---
title: Yapılandırma ve SelectedItem Nesneleri için Otomasyon | Microsoft Dokümanlar
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
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709966"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Yapılandırma ve SelectedItem nesneleri için otomasyon

Visual Studio'da yapı ve seçili öğe işlemlerini otomatikleştirebilirsiniz.

## <a name="automation-for-builds"></a>Yapılar için otomasyon

Yapı veya yapılandırma, uyguladığınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>zaman sağlanan bir otomasyon modeline sahiptir. Daha fazla bilgi için yapı [yapılandırmalarını anlayın.](../../ide/understanding-build-configurations.md)

Bir VSPackage oluşturursanız ve yapılandırma seçeneklerini denetlemek istiyorsanız, otomasyon modelini kullanmanız gerekir.

## <a name="automation-for-selecteditem"></a>SelectedItem için Otomasyon

Visual Studio standart bir uygulama `SelectedItem` içerdiğinden nesne için bir uygulama sağlamanız gerekmez. Ancak, isterseniz nesneyi `SelectedItem` uygulayabilirsiniz. `SelectedItem` Arabirimi içeren bir nesne uygulamanız ve __VSHPROPID `VSITEMID` ayarlı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yönteme bir çağrıyanıtı döndürmeniz [gerekir. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Otomasyon modeline katkıda bulunmak](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
