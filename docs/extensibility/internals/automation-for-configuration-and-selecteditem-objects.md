---
title: Yapılandırma ve SelectedItem Nesneleri için Otomasyon | Microsoft Docs
description: Kabuk Birlikte Çalışma'Visual Studio Configuration ve SelectedItem nesnelerini kullanarak derleme ve seçilen öğe işlemlerini otomatikleştirmeyi öğrenin.
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
ms.openlocfilehash: eac3740444d1c48a196d717e073da035f5920aec468ff216ad22ebdc6cb65918
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359760"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Yapılandırma ve SelectedItem nesneleri için Otomasyon

Derleme ve seçilen öğe işlemlerini Visual Studio.

## <a name="automation-for-builds"></a>Derlemeler için otomasyon

Derleme veya yapılandırma, uygulayan bir otomasyon modeline sahip <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> olur. Daha fazla bilgi için [bkz. Derleme yapılandırmalarını anlama.](../../ide/understanding-build-configurations.md)

VSPackage'i oluşturmak ve yapılandırma seçeneklerini kontrol etmek için otomasyon modelini kullansanız gerekir.

## <a name="automation-for-selecteditem"></a>SelectedItem için Otomasyon

Standart bir uygulama içerdiği için nesne için `SelectedItem` bir uygulama Visual Studio gerekli değildir. Ancak isterseniz nesnesini `SelectedItem` de gerçekleştirebilirsiniz. Arabirimini içeren bir nesnesi uygulamalı ve yöntemi çağrısına yanıt olarak ayarlanmış bir yanıt `SelectedItem` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` [__VSHPROPID. VSHPROPID_ExtSelectedItem.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Otomasyon modeline katkıda bulunun](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
