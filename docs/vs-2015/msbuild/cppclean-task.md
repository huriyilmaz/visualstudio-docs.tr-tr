---
title: CPPClean görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bddba1170cf675b5bde7ab8deed8cce1e7eb57dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196569"
---
# <a name="cppclean-task"></a>CPPClean Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Visual C++ projesi oluşturulduğunda MSBuild tarafından oluşturulan geçici dosyaları siler. Derleme dosyalarını silme işlemi *Temizleme*olarak bilinir.  

## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda **CPPClean** görevinin parametreleri açıklanmaktadır.  

|            Parametre            |                                                                                                Açıklama                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               İsteğe bağlı `ITaskItem[]` çıkış parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılan MSBuild çıkış dosyası öğelerinin dizisini tanımlar.                                |
|          **DoDelete**           |                                                            İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer `true` , geçici derleme dosyalarını temizleyin.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Gerekli `String` parametre.<br /><br /> Temizleyen dosyaların dosya uzantılarının noktalı virgülle ayrılmış bir listesini belirtir.                                             |
|   **Filesexcludedfromcyalın**    |                                                    İsteğe bağlı `String` parametre.<br /><br /> Temizleyememelidir dosyaların noktalı virgülle ayrılmış bir listesini belirtir.                                                    |
|       **FoldersToClean**        | Gerekli `String` parametre.<br /><br /> Temizleyen dizinlerin noktalı virgülle ayrılmış bir listesini belirtir. Tam veya göreli bir yol belirtebilirsiniz ve yol joker karakter simgesini ( **\\** \* ) içerebilir. |

## <a name="remarks"></a>Açıklamalar  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
