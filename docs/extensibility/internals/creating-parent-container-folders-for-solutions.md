---
title: Çözümler için üst kapsayıcı klasörleri oluşturma | Microsoft Docs
description: Bir çözüm içindeki tüm Web projeleri için tek bir kök kaynak denetimi hedefi belirtmek üzere kaynak denetimi eklentisi API 'SI sürüm 1,2 ' i nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c9b3b5c01e9c1ad5de9fbb0a44398d3f7963295
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056850"
---
# <a name="create-parent-container-folders-for-solutions"></a>Çözümler için üst kapsayıcı klasörleri oluşturma
Kaynak denetimi eklentisi API sürümü 1,2 ' de, bir Kullanıcı Çözümdeki tüm Web projeleri için tek bir kök kaynak denetimi hedefi belirtebilir. Bu tek köke süper Birleşik kök (SUR) denir.

 Kaynak denetimi eklentisi API sürümü 1,1 ' de, Kullanıcı kaynak denetimine çok projem çözümü eklediğine göre, kullanıcıdan her Web projesi için bir kaynak denetimi hedefi belirtmesi istenir.

## <a name="new-capability-flags"></a>Yeni yetenek bayrakları
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Yeni işlevler
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kaynak denetimine bir çözüm eklenirken IDE neredeyse her zaman BIR sur klasörü oluşturur. Özellikle, aşağıdaki durumlarda bunu yapar:

- Proje bir dosya paylaşma web projem.

- Proje ve çözüm dosyası için farklı sürücüler vardır.

- Proje ve çözüm dosyası için farklı paylaşımlar vardır.

- Projeler ayrı olarak (kaynak denetimli bir çözümde) eklenmiştir.

' De [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , sur klasörünün adının uzantı olmadan çözüm adıyla aynı olması önerilir. Aşağıdaki tabloda, iki sürümündeki davranış özetlenmektedir.

|Özellik|Kaynak denetimi eklentisi API sürümü 1,1|Kaynak denetimi eklentisi API sürümü 1,2|
|-------------| - | - |
|SCC 'e çözüm ekleme|SccInitialize ()<br /><br /> SccGetProjPath ()<br /><br /> SccGetProjPath ()<br /><br /> SccOpenProject ()|SccInitialize ()<br /><br /> SccGetProjPath ()<br /><br /> Scccreatealt projesi ()<br /><br /> Scccreatealt projesi ()<br /><br /> SccOpenProject ()|
|Kaynak denetimli çözüme proje ekleme|SccGetProjPath ()<br /><br /> OpenProject ()|SccGetParentProjectPath ()<br /><br /> SccOpenProject ()<br /><br />  **Note:**  Visual Studio, bir çözümün bir doğrudan SUR 'in alt öğesi olduğunu varsayar.|

## <a name="examples"></a>Örnekler
 Aşağıdaki tabloda iki örnek listelenmektedir. Her iki durumda da, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  *User_choice* hedef olarak belirtilene kadar, kullanıcıdan kaynak denetimi altındaki çözüm için bir hedef konum istenir. User_choice belirtildiğinde, çözüm ve iki proje, kullanıcıdan kaynak denetimi hedeflerine sormadan eklenir.

|Çözüm içerir|Disk konumlarında|Veritabanı varsayılan yapısı|
|-----------------------|-----------------------|--------------------------------|
|*sln1. sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot $ \Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/web2|
|*sln1. sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\ınetpub\wwwroot\web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/Web1<br /><br /> $/<user_choice>/sln1/win1|

 Bir hata nedeniyle işlemin iptal edilip edilmeyeceğini veya başarısız olup olmamasından bağımsız olarak, SUR klasörü ve alt klasörleri oluşturulur. Bunlar, iptal veya hata koşullarında otomatik olarak kaldırılmaz.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kaynak denetimi eklentisi ve yetenek bayrakları döndürmezse varsayılan sürüm 1,1 davranışına `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` sahiptir. Ayrıca, kullanıcıları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aşağıdaki anahtarın değerini *DWORD: 00000001* olarak ayarlayarak sürüm 1,1 davranışına döndürmeyi seçebilir:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl**  =  *DWORD: 00000001*

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API sürümü 1,2 ' deki yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
