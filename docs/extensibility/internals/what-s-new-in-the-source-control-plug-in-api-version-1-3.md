---
title: Kaynak Kontrol Eklentisi API Sürüm 1.3'te neler&#39;| Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703370"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Kaynak Denetimi Eklentisi API Sürüm 1.3'te Yeni&#39;
Kaynak Denetimi Eklentisi API sürüm 1.3, daha gelişmiş denetim sağlamak için aşağıdaki yeni işlevleri sunar.

## <a name="changes"></a>Değişiklikler
 Aşağıdaki işlevler Kaynak Denetimi Eklentisi API sürümü 1.3 için yenidir:

|İşlev|Genel Bakış|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ek özellik bitlerinin raporedilmesine izin verir|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Sürüm denetim veritabanında yerel diskten daha yeni sürümler bulunan dosyaların incelenmesine izin verir|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Belirtilen dosyalar için ad değişikliklerinin (yeniden adlar, eklemeler ve silmeler) durumunun incelenmesine izin verir|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Sürüm kontrol veritabanında dizinlerin ve dosyaların incelenmesine izin verir|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Sürüm denetim veritabanından geçerli projeye belirli bir dosya listesi ekler|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Belirtilen dosyaların sessiz bir "Get" gerçekleştirir (hiçbir kullanıcı arabirimi gösterilir)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Kullanıcıya özel seçeneklere erişim sağlar|

## <a name="see-also"></a>Ayrıca bkz.
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
