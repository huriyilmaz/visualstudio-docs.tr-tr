---
title: WriteCodeFragment Görev | Microsoft Docs
description: Belirtilen MSBuild parçasından geçici bir kod dosyası oluşturmak için WriteCodeFragment görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e664e8af4d65ec0e629d2a26a307aaf71a6ca12bd411855032b2ca394a160f93
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369442"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment görevi

Belirtilen oluşturulan kod parçasından geçici bir kod dosyası üretir. Dosyayı silemez.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `WriteCodeFragment` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AssemblyAttributes`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Yazacak özniteliklerin açıklaması. Öğe `Include` değeri özniteliğin tam tür adıdır; örneğin, "System.AssemblyVersionAttribute".<br /><br /> Her meta veri, türünde olması gereken bir parametrenin ad-değer `String` çiftidir. Bazı öznitelikler yalnızca konumsal oluşturucu bağımsız değişkenlerine izin eder. Ancak, bu tür bağımsız değişkenleri herhangi bir öznitelikte kullanabilirsiniz. Konum oluşturucu özniteliklerini ayarlamak için "_Parameter1", "_Parameter2" gibi meta veri adlarını kullanın.<br /><br /> Parametre dizini atlanabilir.|
|`Language`|Gerekli `String` parametre.<br /><br /> Oluşturul eklenecek kodun dilini belirtir.<br /><br /> `Language` , CodeDom sağlayıcısının kullanılabilir olduğu herhangi bir dil olabilir; örneğin, "C#" veya "VisualBasic". Yayılan dosya, bu dil için varsayılan dosya adı uzantısına sahip olur.|
|`OutputDirectory`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Oluşturulan kod için hedef klasörü, genellikle ara klasörü belirtir.|
|`OutputFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı çıkış parametresi.<br /><br /> Oluşturulan dosyanın yolunu belirtir. Bu parametre bir dosya adı kullanılarak ayarlanırsa, hedef klasör dosya adının ön ucu olur. Kök kullanılarak ayarlanırsa hedef klasör yoksayılır.<br /><br /> Bu parametre ayarlanmazsa, çıkış dosyası adı hedef klasör, rastgele bir dosya adı ve belirtilen dil için varsayılan dosya adı uzantısıdır.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
