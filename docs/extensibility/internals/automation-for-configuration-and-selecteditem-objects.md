---
title: Yapılandırma ve Selecteditıtem nesneleri için Otomasyon | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709966"
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
