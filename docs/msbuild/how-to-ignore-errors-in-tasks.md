---
title: 'Nasıl yapılır: görevlerdeki hataları yoksayma | Microsoft Docs'
description: MSBuild görevlerinde hataları yoksaymayı ve bir görev hatası oluştuğunda bir yapılandırmanın durmasını veya devam edip etmediğini denetlemek hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 97a2666b32ad7e6bc93865fa36529377652b6453
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436256"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Nasıl yapılır: görevlerdeki hataları yoksayma

Bazen bir derlemeyi belirli görevlerde hatalara karşı dayanıklı olmasını isteyebilirsiniz. Kritik olmayan görevler başarısız olursa, gerekli çıktıyı hala üretebileceğinden, derlemeyi devam ettirmek istersiniz. Örneğin, bir proje `SendMail` her bileşen oluşturulduktan sonra e-posta iletisi göndermek için bir görev kullanıyorsa, posta sunucuları kullanılamadığında ve durum iletileri gönderilemediği zaman bile yapılandırmanın tamamlanmasına devam edebilmesi için kabul edilebilir olarak düşünebilirsiniz. Ya da örneğin, derleme sırasında ara dosyalar silinirse, bu dosyalar silinemese bile, derleme tamamlanana kadar devam etmek için kabul edilebilir olarak düşünebilirsiniz.

## <a name="use-the-continueonerror-attribute"></a>Devam eden özniteliğini kullanma

`ContinueOnError`Öğesinin özniteliği bir `Task` görev hatası oluştuğunda bir yapılandırmanın durmasını veya devam edip etmediğini denetler. Bu öznitelik, derleme devam ettiğinde hataların hata ya da uyarı olarak değerlendirilip değerlendirilmediğini denetler.

`ContinueOnError`Özniteliği aşağıdaki değerlerden birini içerebilir:

- **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.

- **Errportadcontinue**. Bir görev başarısız olduğunda, öğedeki sonraki görevler `Target` ve derleme yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.

- **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğe ve yapı içindeki kalan görevler `Target` yürütülmez ve tüm `Target` öğe ve derleme başarısız olarak kabul edilir.

4,5 ' den önceki .NET Framework sürümleri yalnızca `true` ve değerlerini destekliyordu `false` .

Varsayılan değeri `ContinueOnError` `ErrorAndStop` . Özniteliğini olarak ayarlarsanız `ErrorAndStop` , davranışı proje dosyasını okuyan herkese açık hale getirebilirsiniz.

#### <a name="to-ignore-an-error-in-a-task"></a>Görevdeki bir hatayı yok saymak için

`ContinueOnError`Görevin özniteliğini kullanın. Örneğin:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `Build` hedefin hala çalıştığını ve bir görev başarısız olsa bile derlemenin başarılı olarak kabul edileceğini gösterir `Delete` .

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

- [MSBuild](../msbuild/msbuild.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
