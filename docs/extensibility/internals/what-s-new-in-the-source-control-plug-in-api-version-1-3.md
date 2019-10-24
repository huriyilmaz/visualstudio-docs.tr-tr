---
title: "&#39;Kaynak denetımı eklentisi apı sürümü 1,3 ' deki yenilikler | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f45eeb3c57d5339b1e9fd66951dcbb60970e108
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721583"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>&#39;Kaynak denetımı eklentisi apı sürümü 1,3 ' deki yenilikler
Kaynak denetimi eklentisi API sürümü 1,3, daha gelişmiş denetim sağlamak için aşağıdaki yeni işlevleri sunmaktadır.

## <a name="changes"></a>Değişiklikler
 Aşağıdaki işlevler, kaynak denetimi eklentisi API sürümü 1,3 ' de yenidir:

|İşlev|Genel bakış|
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