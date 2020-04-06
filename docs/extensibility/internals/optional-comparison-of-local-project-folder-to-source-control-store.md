---
title: Proje Klasörünü Kaynak Denetim Deposu ile Karşılaştır | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706859"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>İsteğe Bağlı Olarak Yerel Proje Klasörünün Kaynak Denetimi Deposuyla Karşılaştırılması
Kaynak denetimi Plug-in API 1.2 yerel proje klasörü ve kaynak denetimi arasındaki karşılaştırma [sccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md)fonksiyonları kullanılarak gerçekleştirilir.

 **Solution Explorer**içinde, tek bir dosya yerine bir klasör seçilirse, **karşılaştırma sürümleri** kısayol menüsü kaynak denetim eklentisinde yeni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md) çağırır.

## <a name="new-capability-flags"></a>Yeni Yetenek Bayrakları
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Yeni Fonksiyonlar
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Çalışma `SccDirQueryInfo` dizininin `SccDirDiff` kaynak denetiminde olup olmadığını belirlemek için işlev daha önce çağrılır. İşlev, `SccDirDiff` geçerli yerel dizini ile ilgili kaynak denetim klasörü arasındaki farkları görüntüler. Bu komut, kaynak denetim eklentisinin dizindeki değişikliklerin listesini görüntülemesini ister. Kaynak denetim eklentisi, farklılıkları görüntülemek için kendi kullanıcı kullanıcı aracını sağlar.

> [!NOTE]
> Bu [işlev, SccDiff](../../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Kaynak denetimi eklentisi sağlayıcısı olarak, dizinler için "hızlı diff" işlemini desteklememeyi seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
