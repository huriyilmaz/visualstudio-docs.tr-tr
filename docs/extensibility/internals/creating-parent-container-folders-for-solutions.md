---
title: Çözümler için Üst Kapsayıcı Klasörleri Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709096"
---
# <a name="create-parent-container-folders-for-solutions"></a>Çözümler için ana kapsayıcı klasörleri oluşturma
Kaynak Denetimi Eklentisi API Sürüm 1.2'de, kullanıcı çözüm deki tüm web projeleri için tek bir kök kaynak denetim hedefi belirleyebilir. Bu tek kök, Süper Birleşik Kök (SUR) olarak adlandırılır.

 Kaynak Denetimi Eklentisi API Sürüm 1.1'de, kullanıcı kaynak denetimine çok projeli bir çözüm eklediyse, kullanıcıdan her web projesi için bir kaynak denetim hedefi belirtmesi istenir.

## <a name="new-capability-flags"></a>Yeni yetenek bayrakları
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Yeni işlevler
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, kaynak denetimine bir çözüm eklerken hemen hemen her zaman bir SUR klasörü oluşturur. Özellikle, aşağıdaki durumlarda bunu yapar:

- Proje bir dosya paylaşımı web projesidir.

- Proje ve çözüm dosyası için farklı sürücüler vardır.

- Proje ve çözüm dosyası için farklı paylaşımlar vardır.

- Projeler ayrı olarak (kaynak kontrollü bir çözümde) eklendi.

, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]SUR klasöründeki adın uzantıolmadan çözüm adı ile aynı olması önerilir. Aşağıdaki tabloda iki sürümdeki davranış özetlenmiştir.

|Özellik|Kaynak Kontrol Eklentisi API Sürüm 1.1|Kaynak Kontrol Eklentisi API Sürüm 1.2|
|-------------| - | - |
|SCC'ye çözüm ekleme|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Kaynak kontrollü çözüme proje ekleme|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Not:**  Visual Studio bir çözüm SUR doğrudan bir çocuk olduğunu varsayar.|

## <a name="examples"></a>Örnekler
 Aşağıdaki tabloda iki örnek listeleilmektedir. Her iki durumda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da, *user_choice* hedef olarak belirtilene kadar kullanıcı kaynak denetimi altında çözüm için bir hedef konumu için istenir. user_choice belirtildiğinde, çözüm ve iki proje kaynak denetim hedefleri için kullanıcı istenmeden eklenir.

|Çözüm içerir|Disk konumlarında|Veritabanı varsayılan yapısı|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\sunucu\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 SUR klasörü ve alt klasörleri, işlemin iptal edilip edilmediğine veya bir hata nedeniyle başarısız olup olmadığına bakılmaksızın oluşturulur. İptal veya hata koşullarında otomatik olarak kaldırılmaz.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kaynak denetim eklentisi geri dönmüyorsa `SCC_CAP_CREATESUBPROJECT` ve `SCC_CAP_GETPARENTPROJECT` özellik bayrakları kullanıyorsa Sürüm 1.1 davranışı varsayılan. Ayrıca, kullanıcılar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *dword:00000001*için aşağıdaki anahtarın değerini ayarlayarak Sürüm 1.1 davranışına geri dönmek için seçebilirsiniz:

 **[HKEY_CURRENT_USER\Yazılım\Microsoft\VisualStudio\8.0\Kaynak Denetimi] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API Sürüm 1.2'deki yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
