---
title: CPPClean Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634350"
---
# <a name="cppclean-task"></a>CPPClean Görevi

Bir C++ projesi oluşturulurken MSBuild'in oluşturduğu geçici dosyaları siler. Yapı dosyalarını silme işlemi *temizleme*olarak bilinir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **CPPClean** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Silinen Dosyalar**|İsteğe bağlı `ITaskItem[]` çıktı parametresi.<br /><br /> Görevler tarafından tüketilebilen ve yayılabilen bir dizi MSBuild çıktı dosyası öğesi tanımlar.|
|**DoDelete**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`geçici yapı dosyalarını temizleyin.|
|**FilePatternstodeleteonClean**|Gerekli `String` parametre.<br /><br /> Temizleyecek dosyaların dosya uzantılarının yarı sütunlu sınırlı bir listesini belirtir.|
|**FilesExcludedFromClean**|İsteğe bağlı `String` parametre.<br /><br /> Temizlenmemesi gereken yarı sütunlu sınırlı bir dosya listesi belirtir.|
|**KlasörlerToClean**|Gerekli `String` parametre.<br /><br /> Temizleyecek yarı sütunlu dizinler listesini belirtir. Tam veya göreceli bir yol belirtebilirsiniz ve yol joker karakter simgesini (*) içerebilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
