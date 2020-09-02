---
title: Yerel proje klasörünün kaynak denetimi deposuna isteğe bağlı karşılaştırması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be26b4195e0db7b3b78fcc2223ff2a6f8bde47d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819037"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>İsteğe Bağlı Olarak Yerel Proje Klasörünün Kaynak Denetimi Deposuyla Karşılaştırılması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi eklentisi API 1,2 ' de, yerel proje klasörü ve kaynak denetimi arasındaki karşılaştırma [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md)işlevleri kullanılarak gerçekleştirilir.  
  
 **Çözüm Gezgini**içinde, tek bir dosya yerine bir klasör seçilirse **sürümleri Karşılaştır** kısayol menüsü, kaynak denetimi eklentisindeki yeni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md) öğesini çağırır.  
  
## <a name="new-capability-flags"></a>Yeni yetenek bayrakları  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Yeni Işlevler  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`İşlevi, `SccDirDiff` çalışma dizininin kaynak denetimli olup olmadığı saptanmadan önce çağrılır. `SccDirDiff`İşlevi, geçerli yerel dizin ile buna karşılık gelen kaynak denetimi klasörü arasındaki farkları görüntüler. Bu komut, kaynak denetimi eklentisinin dizin üzerinde yapılan değişikliklerin listesini görüntülemesini ister. Kaynak denetimi eklentisi, farkları göstermek için kendi Kullanıcı arabirimini sağlar.  
  
> [!NOTE]
> Bu işlev, [SccDiff](../../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Kaynak denetimi eklenti sağlayıcısı olarak, dizinler için "hızlı fark" işlemini desteklemeyi tercih edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
