---
title: WriteCodeFragment Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ab604b23a99ab2dd62adca6076168fe264ab1b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630698"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment görevi

Belirtilen oluşturulan kod parçasından geçici bir kod dosyası oluşturur. Dosyayı silmez.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `WriteCodeFragment` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AssemblyAttributes`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yazılması gereken özniteliklerin açıklaması. Madde `Include` değeri özniteliğin tam tür adıdır, örneğin, "System.AssemblyVersionAttribute".<br /><br /> Her meta veri, bir parametrenin ad değeri çiftidir `String`ve bu türde olmalıdır. Bazı öznitelikler yalnızca konumsal oluşturucu bağımsız değişkenler sağlar. Ancak, bu tür bağımsız değişkenleri herhangi bir öznitelik kullanabilirsiniz. Konum oluşturucu öznitelikleri ayarlamak için "_Parameter1", "_Parameter2" gibi meta veri adlarını kullanın.<br /><br /> Parametre dizini atlanamaz.|
|`Language`|Gerekli `String` parametre.<br /><br /> Oluşturmak için kodun dilini belirtir.<br /><br /> `Language`codedom sağlayıcısının (örneğin, "C#" veya "VisualBasic" gibi) kullanılabildiği herhangi bir dil olabilir. Yayılan dosya, bu dil için varsayılan dosya adı uzantısına sahip olacaktır.|
|`OutputDirectory`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Oluşturulan kodun hedef klasörünü( genellikle ara klasörü) belirtir.|
|`OutputFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıktı parametresi.<br /><br /> Oluşturulan dosyanın yolunu belirtir. Bu parametre bir dosya adı kullanılarak ayarlanırsa, hedef klasör dosya adına hazırlanır. Bir kök kullanılarak ayarlanırsa, hedef klasörü yoksayılır.<br /><br /> Bu parametre ayarlanmamışsa, çıktı dosyası adı hedef klasörü, rasgele bir dosya adı ve belirtilen dil için varsayılan dosya adı uzantısıdır.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
