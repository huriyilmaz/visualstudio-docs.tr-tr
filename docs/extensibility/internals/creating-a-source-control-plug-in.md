---
title: Kaynak Kontrol Eklentisi Oluşturma | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709180"
---
# <a name="create-a-source-control-plug-in"></a>Kaynak kontrol eklentisi oluşturma
Visual Studio SDK, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamına (IDE) kaynak denetimi özelliği eklemenize olanak tanıyan kaynaklar sağlar. Bu belgede özetlenen Kaynak Denetim Eklentisi API'si ile uyumlu herhangi bir eklenti DLL kullanmanıza olanak sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [başlarken](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Kaynak denetimi eklentisinin nasıl yüklenir ve şu anda kullanılabilir Olan Kaynak Denetimi Eklentisi API sürümlerini vurgular.

- [Mimari](../../extensibility/internals/source-control-plug-in-architecture.md)

 Kaynak denetim eklentisinin IDE ile tümleştirilmesini açıklamak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için bir mimari diyagramı kullanır.

- [Test kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Kaynak denetim eklentisinin yüklenmesi ve çalıştırılaması hakkında rehberlik sağlar.

## <a name="related-sections"></a>İlgili bölümler
- [Bir kaynak denetimi vspackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Yalnızca kaynak denetimi işlevselliği sağlamakla kalmamış, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aynı zamanda kaynak denetimi ui'sini değiştiren bir kaynak denetimi VSPackage'ın nasıl oluşturulabildiğini tartışır.

- [Kaynak kontrol eklentileri](../../extensibility/source-control-plug-ins.md)

 Kaynak Denetimi Eklentisi API'sindeki tüm öğelerin tam bir listesini sağlar.

- [Kaynak denetimi](../../extensibility/internals/source-control.md)

 Kaynak denetiminin tümleşik bir özelliği olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uygulanması na yönelik seçenekleri tartışır.
