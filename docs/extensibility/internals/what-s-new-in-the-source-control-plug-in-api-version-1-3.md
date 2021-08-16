---
title: Kaynak &apos; denetimi eklentisi API 1.3'te yapılan değişiklikler
description: Daha gelişmiş denetim sağlamak için yeni işlevlerin tanıt olduğu Kaynak Denetimi Eklentisi API'si sürüm 1.3'te neler olduğu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5b7b200a45dd0fe87ff399917e196e00b3c365cdff854c5caa01ba22ab30672d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359123"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Kaynak&#39;API'si Sürüm 1.3'te Yapılan Yeni Değişiklikler
Kaynak Denetimi Eklentisi API'si sürüm 1.3, daha gelişmiş denetim sağlamak için aşağıdaki yeni işlevleri sunar.

## <a name="changes"></a>Değişiklikler
 Aşağıdaki işlevler Kaynak Denetimi Eklentisi API'si sürüm 1.3'te yenidir:

|İşlev|Genel Bakış|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ek özellik bitlerinin rapor özeliklerini sağlar|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Sürüm denetimi veritabanında yerel diskten daha yeni sürümleri olan dosyaların incelemesine izin verir|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Belirtilen dosyalar için ad değişikliklerinin (yeniden adlandırmalar, eklemeler ve silmeler) durumunun incelemesine izin verir|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Sürüm denetimi veritabanındaki dizinlerin ve dosyaların incelemesine izin verir|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Sürüm denetimi veritabanından geçerli projeye belirtilen dosya listesini ekler|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Belirtilen dosyaların sessiz bir "Get" işlemini gerçekleştirir (kullanıcı arabirimi gösterilmez)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Kullanıcıya özgü seçeneklere erişime izin verir|

## <a name="see-also"></a>Ayrıca bkz.
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
