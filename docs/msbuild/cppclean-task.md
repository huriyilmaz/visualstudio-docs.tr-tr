---
title: CPPClean Görev | Microsoft Docs
description: Bu makalede, bir C++ projesi yerleşik olduğunda bu dosyanın oluşturduğu geçici MSBuild silmek için kullanılan CPPClean görevi açıklanmıştır.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 65437104a04de8fe08f21b077a093483ec3209df
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054957"
---
# <a name="cppclean-task"></a>CPPClean Görevi

Bir C++ projesi MSBuild oluşturduğu geçici dosyaları siler. Derleme dosyalarını silme işlemi temizleme olarak *bilinir.*

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **CPPClean** görevinin parametreleri açık almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**DeletedFiles**|İsteğe `ITaskItem[]` bağlı çıkış parametresi.<br /><br /> Görevler tarafından MSBuild bir çıkış dosyası öğeleri dizisi tanımlar.|
|**DoDelete**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` geçici derleme dosyalarını temizleyin.|
|**FilePatternsToDeleteOnClean**|Gerekli `String` parametre.<br /><br /> Temizlenir dosyaların dosya uzantılarının noktalı virgülle ayrılmış listesini belirtir.|
|**FilesExcludedFromClean**|İsteğe `String` bağlı parametre.<br /><br /> Temiz gerek olmayan noktalı virgülle ayrılmış dosya listesini belirtir.|
|**FoldersToClean**|Gerekli `String` parametre.<br /><br /> Temizlenir dizinlerin noktalı virgülle ayrılmış listesini belirtir. Tam veya göreli bir yol belirterek joker karakter simgesi (*) kullanabilirsiniz.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
