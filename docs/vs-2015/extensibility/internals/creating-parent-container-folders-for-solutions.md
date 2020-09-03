---
title: Çözümler için üst kapsayıcı klasörleri oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196935"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Çözümler için Üst Kapsayıcı Klasörleri Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi eklentisi API sürümü 1,2 ' de, bir Kullanıcı Çözümdeki tüm Web projeleri için tek bir kök kaynak denetimi hedefi belirtebilir. Bu tek köke süper Birleşik kök (SUR) denir.  
  
 Kaynak denetimi eklentisi API sürümü 1,1 ' de, Kullanıcı kaynak denetimine çok projem çözümü eklediğine göre, kullanıcıdan her Web projesi için bir kaynak denetimi hedefi belirtmesi istenir.  
  
## <a name="new-capability-flags"></a>Yeni yetenek bayrakları  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Yeni Işlevler  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kaynak denetimine bir çözüm eklenirken IDE neredeyse her zaman BIR sur klasörü oluşturur. Özellikle, aşağıdaki durumlarda bunu yapar:  
  
- Proje bir dosya paylaşma web projem.  
  
- Proje ve çözüm dosyası için farklı sürücüler vardır.  
  
- Proje ve çözüm dosyası için farklı paylaşımlar vardır.  
  
- Projeler ayrı olarak (kaynak denetimli bir çözümde) eklenmiştir.  
  
  İçinde, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sur klasörünün adının uzantı olmadan çözüm adıyla aynı olması önerilir. Aşağıdaki tabloda, iki sürümündeki davranış özetlenmektedir.  
  
|Öne çıkan özelliği|tSource denetim eklentisi API sürümü 1,1|Kaynak denetimi eklentisi API sürümü 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|SCC 'e çözüm ekleme|SccInitialize ()<br /><br /> SccGetProjPath ()<br /><br /> SccGetProjPath ()<br /><br /> SccOpenProject ()|SccInitialize ()<br /><br /> SccGetProjPath ()<br /><br /> Scccreatealt projesi ()<br /><br /> Scccreatealt projesi ()<br /><br /> SccOpenProject ()|  
|Kaynak denetimli çözüme proje ekleme|SccGetProjPath ()<br /><br /> OpenProject ()|SccGetParentProjectPath ()<br /><br /> SccOpenProject () **Note:**  Visual Studio, bir çözümün BIR doğrudan sur 'in alt öğesi olduğunu varsayar.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki tabloda iki örnek listelenmektedir. Her iki durumda da, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  *User_choice* hedef olarak belirtilene kadar, kullanıcıdan kaynak denetimi altındaki çözüm için bir hedef konum istenir. User_choice belirtildiğinde, çözüm ve iki proje, kullanıcıdan kaynak denetimi hedeflerine sormadan eklenir.  
  
|Çözüm içerir|Disk konumlarında|Veritabanı varsayılan yapısı|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot $ \web2|$/*User_choice*/sln1<br /><br /> $/*User_choice*/C/Web1<br /><br /> $/*User_choice*/web2|  
|sln1. sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\ınetpub\wwwroot\web1<br /><br /> C:\solutions\sln1\Win1|$/*User_choice*/sln1<br /><br /> $/*User_choice*/D/Web1<br /><br /> $/*User_choice*/sln1/win1|  
  
 Bir hata nedeniyle işlemin iptal edilip edilmeyeceğini veya başarısız olup olmamasından bağımsız olarak, SUR klasörü ve alt klasörleri oluşturulur. Bunlar, iptal veya hata koşullarında otomatik olarak kaldırılmaz.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kaynak denetimi eklentisi ve yetenek bayrakları döndürmezse varsayılan sürüm 1,1 davranışına `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` sahiptir. Ayrıca, kullanıcıları [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aşağıdaki anahtarın değerini DWORD: 00000001 olarak ayarlayarak sürüm 1,1 davranışına döndürmeyi seçebilir:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
