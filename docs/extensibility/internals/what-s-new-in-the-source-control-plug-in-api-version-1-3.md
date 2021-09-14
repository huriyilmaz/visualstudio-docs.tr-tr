---
title: "&apos;Kaynak denetimi EKLENTISI apı 1,3 ' deki yenilikler"
description: Daha gelişmiş denetim sağlamak için yeni işlevleri sunan kaynak denetimi eklentisi API 'SI sürüm 1,3 ' deki yenilikler hakkında bilgi edinin.
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
ms.openlocfilehash: 1b3ee614a0f754307c37e5d48dfb3d9f461ec432
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726914"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Kaynak denetimi eklentisi API sürüm 1,3 ' deki yenilikler&#39;
Kaynak denetimi eklentisi API sürümü 1,3, daha gelişmiş denetim sağlamak için aşağıdaki yeni işlevleri sunmaktadır.

## <a name="changes"></a>Değişiklikler
 Aşağıdaki işlevler, kaynak denetimi eklentisi API sürümü 1,3 ' de yenidir:

|İşlev|Genel Bakış|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ek özellik bitlerinin raporlanmasını sağlar|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Sürüm denetimi veritabanında yeni sürümlere sahip dosyaların yerel diskten incelemesini sağlar|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Belirtilen dosyalar için ad değişikliklerinin (yeniden adlandırmalar, eklemeler ve silmeler) durumunun incelemesini sağlar|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Sürüm denetimi veritabanındaki dizinlerin ve dosyaların incelemesini sağlar|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Sürüm denetim veritabanından geçerli projeye belirtilen dosya listesini ekler|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Belirtilen dosyaların sessiz bir "Al" işlemini gerçekleştirir (Kullanıcı arabirimi gösterilmez)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Kullanıcıya özgü seçeneklere erişime izin verir|

## <a name="see-also"></a>Ayrıca bkz.
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
