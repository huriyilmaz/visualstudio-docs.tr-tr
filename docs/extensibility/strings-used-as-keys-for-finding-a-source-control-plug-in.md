---
title: Kaynak denetimi eklentisini bulmak için anahtar olarak kullanılan dizeler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07962ff9e0f9371b1fc308a35600a6819602b4f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719448"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler
Aşağıdaki dizeler, kaynak denetimi eklentisi hakkındaki bilgileri bulmak için kayıt defterine erişim anahtarlardır.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH` ve `STR_SCCPROVIDERNAME` kayıt defteri anahtarları veya bir DLL 'yi Visual Studio için kaynak denetimi eklentisi olarak kaydetmek için kullanılan değerlerdir.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE` ve `SCC_STATUS_FILE`, MSSCCPRJ biçimini tanımlamakta kullanılır. SCC dosyası.

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