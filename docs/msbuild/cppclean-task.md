---
title: CPPClean görevi | Microsoft Docs
description: Bu makalede, bir C++ projesi oluşturulduğunda MSBuild tarafından oluşturulan geçici dosyaları silmek için kullanılan CPPClean görevi açıklanır.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5b3d48c4556cfd05e5ce3f2b893b3f0e9a07226
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901432"
---
# <a name="cppclean-task"></a>CPPClean Görevi

Bir C++ projesi yapılandırıldığında MSBuild 'in oluşturduğu geçici dosyaları siler. Derleme dosyalarını silme işlemi *Temizleme* olarak bilinir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **CPPClean** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**DeletedFiles**|İsteğe bağlı `ITaskItem[]` çıkış parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılan MSBuild çıkış dosyası öğelerinin dizisini tanımlar.|
|**DoDelete**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer `true` , geçici derleme dosyalarını temizleyin.|
|**FilePatternsToDeleteOnClean**|Gerekli `String` parametre.<br /><br /> Temizleyen dosyaların dosya uzantılarının noktalı virgülle ayrılmış bir listesini belirtir.|
|**Filesexcludedfromcyalın**|İsteğe bağlı `String` parametre.<br /><br /> Temizleyememelidir dosyaların noktalı virgülle ayrılmış bir listesini belirtir.|
|**FoldersToClean**|Gerekli `String` parametre.<br /><br /> Temizleyen dizinlerin noktalı virgülle ayrılmış bir listesini belirtir. Tam veya göreli bir yol belirtebilirsiniz ve yol joker karakter simgesini (*) içerebilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
