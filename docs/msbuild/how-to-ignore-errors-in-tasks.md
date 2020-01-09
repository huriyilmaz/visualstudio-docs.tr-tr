---
title: 'Nasıl yapılır: görevlerdeki hataları yoksayma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: be8b4a6845e8fd14a0649f4134bcc26d8e1ad08e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574957"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Nasıl yapılır: görevlerdeki hataları yoksayma
Bazen bir derlemeyi belirli görevlerde hatalara karşı dayanıklı olmasını isteyebilirsiniz. Kritik olmayan görevler başarısız olursa, gerekli çıktıyı hala üretebileceğinden, derlemeyi devam ettirmek istersiniz. Örneğin, bir proje her bileşen oluşturulduktan sonra bir e-posta iletisi göndermek için bir `SendMail` görevi kullanıyorsa, posta sunucuları kullanılamadığında ve durum iletileri gönderilemediği zaman bile yapılandırmanın tamamlanmasına devam edebilmesi için kabul edilebilir olarak düşünebilirsiniz. Ya da örneğin, derleme sırasında ara dosyalar silinirse, bu dosyalar silinemese bile, derleme tamamlanana kadar devam etmek için kabul edilebilir olarak düşünebilirsiniz.

## <a name="use-the-continueonerror-attribute"></a>Devam eden özniteliğini kullanma
`Task` öğesinin `ContinueOnError` özniteliği bir görev hatası oluştuğunda bir yapılandırmanın durmasını veya devam edip etmediğini denetler. Bu öznitelik, derleme devam ettiğinde hataların hata ya da uyarı olarak değerlendirilip değerlendirilmediğini denetler.

`ContinueOnError` özniteliği aşağıdaki değerlerden birini içerebilir:

- **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.

- **Errportadcontinue**. Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.

- **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki kalan görevler yürütülmez ve tüm `Target` öğesi ve derleme başarısız olduğu kabul edilir.

4,5 öncesindeki .NET Framework sürümleri yalnızca `true` ve `false` değerlerini destekliyordu.

`ContinueOnError` varsayılan değeri `ErrorAndStop`. Özniteliği `ErrorAndStop`olarak ayarlarsanız, davranışı proje dosyasını okuyan herkese açık hale getirebilirsiniz.

#### <a name="to-ignore-an-error-in-a-task"></a>Görevdeki bir hatayı yok saymak için

Görevin `ContinueOnError` özniteliğini kullanın. Örneğin:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Örnek
Aşağıdaki kod örneği, `Delete` görevi başarısız olsa bile `Build` hedefinin hala çalıştığını ve derlemenin başarılı olarak kabul edileceğini gösterir.

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
