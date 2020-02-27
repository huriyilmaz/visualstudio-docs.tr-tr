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
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634350"
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
|**Filesexcludedfromcyalın**|İsteğe bağlı `String` parametresi.<br /><br /> Temizleyememelidir dosyaların noktalı virgülle ayrılmış bir listesini belirtir.|
|**FoldersToClean**|Gerekli `String` parametresi.<br /><br /> Temizleyen dizinlerin noktalı virgülle ayrılmış bir listesini belirtir. Tam veya göreli bir yol belirtebilirsiniz ve yol joker karakter simgesini (*) içerebilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
