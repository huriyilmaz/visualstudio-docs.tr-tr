---
title: Project klasörünü kaynak denetimi deposu ile karşılaştırın | Microsoft Docs
description: Kaynak denetimi eklentisi API 'sinde, yerel proje klasörü ve kaynak denetimi arasındaki karşılaştırma SccDirQueryInfo ve SccDirDiff kullanılarak gerçekleştirilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 76d57b288a221b2b7e89494605aaccd4df752821
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063115"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>İsteğe Bağlı Olarak Yerel Proje Klasörünün Kaynak Denetimi Deposuyla Karşılaştırılması
Kaynak denetimi eklentisi API 1,2 ' de, yerel proje klasörü ve kaynak denetimi arasındaki karşılaştırma [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md)işlevleri kullanılarak gerçekleştirilir.

 **Çözüm Gezgini** içinde, tek bir dosya yerine bir klasör seçilirse **sürümleri Karşılaştır** kısayol menüsü, kaynak denetimi eklentisindeki yeni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md) öğesini çağırır.

## <a name="new-capability-flags"></a>Yeni yetenek bayrakları
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Yeni Işlevler
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 `SccDirQueryInfo`İşlevi, `SccDirDiff` çalışma dizininin kaynak denetimli olup olmadığı saptanmadan önce çağrılır. `SccDirDiff`İşlevi, geçerli yerel dizin ile buna karşılık gelen kaynak denetimi klasörü arasındaki farkları görüntüler. Bu komut, kaynak denetimi eklentisinin dizin üzerinde yapılan değişikliklerin listesini görüntülemesini ister. Kaynak denetimi eklentisi, farkları göstermek için kendi Kullanıcı arabirimini sağlar.

> [!NOTE]
> Bu işlev, [SccDiff](../../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Kaynak denetimi eklenti sağlayıcısı olarak, dizinler için "hızlı fark" işlemini desteklemeyi tercih edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
