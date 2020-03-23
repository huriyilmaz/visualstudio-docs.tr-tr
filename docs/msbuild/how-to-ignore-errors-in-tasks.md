---
title: 'Nasıl Yapilir: Görevlerdeki Hataları Yoksay | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 9899b7367e6ae9255755ae04fe06d8c8733043ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633830"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Nasıl yapilir: Görevlerdeki hataları yoksay

Bazen bir yapının belirli görevlerdeki hatalara toleranslı olmasını istersiniz. Bu kritik olmayan görevler başarısız olursa, gerekli çıktıyı yine de üretebildiği için yapının devam etmesini istersiniz. Örneğin, bir proje her `SendMail` bileşen oluşturulmadan sonra bir e-posta iletisi göndermek için bir görev kullanıyorsa, posta sunucuları kullanılamıyorsa ve durum iletileri gönderilmese bile yapının tamamlanmasını kabul edilebilir olarak düşünebilirsiniz. Veya, örneğin, ara dosyalar genellikle yapı sırasında silinirse, bu dosyalar silinemese bile yapının tamamlanmasını kabul edilebilir olarak düşünebilirsiniz.

## <a name="use-the-continueonerror-attribute"></a>ContinueOnError özniteliğini kullanma

Öğenin `ContinueOnError` `Task` özniteliği, bir görev hatası oluştuğunda bir yapının durup durmadığını veya devam edip etmediğini denetler. Bu öznitelik, yapı devam ettiğinde hataların hata veya uyarı olarak kabul edilip edilemeyeceğini de denetler.

Öznitelik `ContinueOnError` aşağıdaki değerlerden birini içerebilir:

- **WarnAndContinue** veya **doğru**. Bir görev başarısız olduğunda, [Hedef](../msbuild/target-element-msbuild.md) öğe ve yapısonraki görevler yürütmeye devam eder ve görevden gelen tüm hatalar uyarı olarak kabul edilir.

- **HataandContinue**. Bir görev başarısız olduğunda, `Target` öğe ve yapı sonraki görevler yürütmeye devam eder ve görevden tüm hatalar hata olarak kabul edilir.

- **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, `Target` öğe ve yapıda kalan görevler yürütülmez ve tüm `Target` öğe ve yapı başarısız olmuş olarak kabul edilir.

.NET Framework'ün 4.5'ten önceki `true` `false` sürümleri yalnızca değerleri ve değerleri desteklemişti.

Varsayılan `ContinueOnError` değeri. `ErrorAndStop` Özniteliği `ErrorAndStop`, proje dosyasını okuyan herkese davranışı açık hale getirin.

#### <a name="to-ignore-an-error-in-a-task"></a>Görevdeki bir hatayı yok saymak için

Görevin `ContinueOnError` özniteliğini kullanın. Örnek:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, görev `Build` başarısız olsa bile hedefin hala çalıştığını `Delete` ve yapının başarılı olarak kabul edilir olduğunu göstermektedir.

```xml
<Project DefaultTargets="FakeBuild"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Files Include="*.obj"/>
    </ItemGroup>
    <Target Name="Clean">
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
    </Target>

    <Target Name="FakeBuild" DependsOnTargets="Clean">
        <Message Text="Building after cleaning..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Msbuild](../msbuild/msbuild.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
