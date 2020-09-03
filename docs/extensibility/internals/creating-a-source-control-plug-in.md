---
title: Kaynak denetimi eklentisi oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709180"
---
# <a name="create-a-source-control-plug-in"></a>Kaynak denetimi eklentisi oluşturma
Visual Studio SDK, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamına (IDE) kaynak denetimi özelliği eklemenize olanak sağlayan kaynaklar sağlar. Bu belgede özetlenen kaynak denetimi eklentisi API 'siyle uyumlu herhangi bir eklenti DLL 'SI kullanmanıza olanak sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Kullanmaya başlama](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Kaynak denetimi eklentisinin nasıl yükleneceğini ve şu anda kullanılabilir kaynak denetimi eklentisi API sürümlerini vurgulamaları açıklanmaktadır.

- [Mimari](../../extensibility/internals/source-control-plug-in-architecture.md)

 IDE ile bir kaynak denetimi eklentisinin tümleştirilmesini açıklamak için bir mimari diyagramı kullanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Kaynak denetim eklentisinin yüklemesinin ve işleminin nasıl test yapılacağı hakkında rehberlik sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Yalnızca kaynak denetimi işlevselliği sağlayan ancak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi kullanıcı arabirimini değiştiren bir kaynak denetimi VSPackage oluşturmayı açıklar.

- [Kaynak denetimi eklentileri](../../extensibility/source-control-plug-ins.md)

 Kaynak denetimi eklentisi API 'sindeki tüm öğelerin tam bir listesini sağlar.

- [Kaynak denetimi](../../extensibility/internals/source-control.md)

 ' Nin tümleşik özelliği olarak kaynak denetimi uygulama seçeneklerini açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
