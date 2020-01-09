---
title: CPPClean görevi | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 827014e04c23239274e31b994fd0178cbe8e5883
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596079"
---
# <a name="cppclean-task"></a>CPPClean Görevi
Bir C++ proje oluşturulduğunda MSBuild tarafından oluşturulan geçici dosyaları siler. Derleme dosyalarını silme işlemi *Temizleme*olarak bilinir.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda **CPPClean** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**DeletedFiles**|İsteğe bağlı `ITaskItem[]` çıkış parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılan MSBuild çıkış dosyası öğelerinin dizisini tanımlar.|
|**DoDelete**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, geçici derleme dosyalarını temizleyin.|
|**FilePatternsToDeleteOnClean**|Gerekli `String` parametresi.<br /><br /> Temizleyen dosyaların dosya uzantılarının noktalı virgülle ayrılmış bir listesini belirtir.|
|**FilesExcludedFromClean**|İsteğe bağlı `String` parametresi.<br /><br /> Temizleyememelidir dosyaların noktalı virgülle ayrılmış bir listesini belirtir.|
|**FoldersToClean**|Gerekli `String` parametresi.<br /><br /> Temizleyen dizinlerin noktalı virgülle ayrılmış bir listesini belirtir. Tam veya göreli bir yol belirtebilirsiniz ve yol joker karakter simgesini (*) içerebilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
