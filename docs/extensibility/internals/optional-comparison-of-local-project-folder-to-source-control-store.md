---
title: Proje klasörünü kaynak denetimi deposu ile karşılaştırın | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726121"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>İsteğe Bağlı Olarak Yerel Proje Klasörünün Kaynak Denetimi Deposuyla Karşılaştırılması
Kaynak denetimi eklentisi API 1,2 ' de, yerel proje klasörü ve kaynak denetimi arasındaki karşılaştırma [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md)işlevleri kullanılarak gerçekleştirilir.

 **Çözüm Gezgini**içinde, tek bir dosya yerine bir klasör seçilirse **sürümleri Karşılaştır** kısayol menüsü, kaynak denetimi eklentisindeki yeni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md) öğesini çağırır.

## <a name="new-capability-flags"></a>Yeni yetenek bayrakları
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Yeni Işlevler
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 @No__t_0 işlevi, çalışma dizininin kaynak denetimli olup olmadığını anlamak için `SccDirDiff` önce çağrılır. @No__t_0 işlevi, geçerli yerel dizin ile buna karşılık gelen kaynak denetimi klasörü arasındaki farkları görüntüler. Bu komut, kaynak denetimi eklentisinin dizin üzerinde yapılan değişikliklerin listesini görüntülemesini ister. Kaynak denetimi eklentisi, farkları göstermek için kendi Kullanıcı arabirimini sağlar.

> [!NOTE]
> Bu işlev, [SccDiff](../../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Kaynak denetimi eklenti sağlayıcısı olarak, dizinler için "hızlı fark" işlemini desteklemeyi tercih edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)