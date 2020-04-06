---
title: Kaynak Kontrol Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeleri | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699709"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler
Aşağıdaki dizeleri kaynak denetim eklentisi hakkında bilgi bulmak için kayıt defterine erişmek için anahtarlardır.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`, `STR_SCCPROVIDERNAME` , , ve bir DLL'yi Visual Studio için kaynak denetim eklentisi olarak kaydetmek için kullanılan kayıt defteri anahtarları veya değerleridir.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` , , ve MSSCCPRJ biçimini tanımlamak için kullanılır. SCC dosyası.

## <a name="string-keys-and-values"></a>String Tuşları ve Değerleri

|Anahtar|Değer|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Yazılım\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|SağlayıcıRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Kaynak Kodu Kontrolü|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|Scc|
|`SCC_FILE_SIGNATURE`|Kaynak kodu denetim dosyası|
|`SCC_NSE`|Ad alanı uzantısı|
|`SCC_NSE_PREFIX`|Protokal Önek|
|`SCC_NSE_DisableOpenSCC`|Devre Dışı AçıkKaynakKontrol|
|`STR_SCCHELPCOLLECTION`|Yardım Koleksiyonu|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Yazılım\Microsoft\SourceSafe|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
- [Nasıl Yapılır: Kaynak Denetimi Eklentisi Yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)
