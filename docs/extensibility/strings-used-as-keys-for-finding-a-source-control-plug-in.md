---
title: Kaynak denetimi eklentisini bulmak için anahtar olarak kullanılan dizeler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699709"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler
Aşağıdaki dizeler, kaynak denetimi eklentisi hakkındaki bilgileri bulmak için kayıt defterine erişim anahtarlardır.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` ve, `STR_SCCPROVIDERNAME` bir dll 'yi Visual Studio için kaynak denetim eklentisi olarak kaydetmek için kullanılan kayıt defteri anahtarları veya değerlerdir.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` ve, `SCC_STATUS_FILE` Mssccprj biçimini tanımlamakta kullanılır. SCC dosyası.

## <a name="string-keys-and-values"></a>Dize anahtarları ve değerleri

|Anahtar|Değer|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Kaynak kodu denetimi|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|Mssccprj. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Kaynak kodu denetim dosyası|
|`SCC_NSE`|Ad alanı uzantısı|
|`SCC_NSE_PREFIX`|Protocal öneki|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
- [Nasıl Yapılır: Kaynak Denetimi Eklentisi Yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)
