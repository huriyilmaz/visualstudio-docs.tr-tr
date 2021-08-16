---
title: 'Nasıl |: Görev Görev | Microsoft Docs'
description: Bir görev hatası oluştuğunda derlemenin MSBuild devam edip etmemeyi denetlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.openlocfilehash: 3f40805c7798fbd4e93a0467ef6137d2ea0956d481821db25efb475a41e1a149
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397663"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Nasıllı: Görevlerde hataları yoksayma

Bazen bir derlemenin belirli görevlerde hatalara karşı karşı güçlü olması gerekir. Bu kritik olmayan görevler başarısız olursa, derlemenin yine de gerekli çıkışı üretmeye devam eder. Örneğin, bir proje her bileşen hazırlandıktan sonra e-posta iletisi göndermek için bir görev kullanıyorsa, posta sunucuları kullanılamasa ve durum iletileri gönderilemiyor olsa bile derlemenin tamamlanmasını kabul edilebilir olarak `SendMail` düşünebilirsiniz. Veya, örneğin, ara dosyalar genellikle derleme sırasında silinirse, bu dosyalar silinene kadar derlemenin tamamlanmasını kabul edilebilir olarak düşünebilirsiniz.

## <a name="use-the-continueonerror-attribute"></a>ContinueOnError özniteliğini kullanma

öğesinin `ContinueOnError` `Task` özniteliği, bir görev hatası oluştuğunda derlemenin dur mu yoksa devam mı olduğunu kontrol eder. Bu öznitelik ayrıca derleme devam ederken hataların hata veya uyarı olarak kabul edilebilir olup olmadığını da kontrol eder.

özniteliği `ContinueOnError` aşağıdaki değerlerden birini içerebilir:

- **WarnAndContinue veya** **true**. Bir görev başarısız olduğunda, [Target](../msbuild/target-element-msbuild.md) öğesinde ve derlemede sonraki görevler yürütülebilir ve görevdeki tüm hatalar uyarı olarak kabul edilir.

- **ErrorAndContinue**. Bir görev başarısız olduğunda, öğesinde ve derlemede sonraki görevler yürütülebilir ve `Target` görevdeki tüm hatalar hata olarak kabul edilir.

- **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğesinde ve derlemede kalan görevler yürütülmez ve tüm öğe ile `Target` `Target` derlemenin başarısız olduğu kabul edilir.

4.5'.NET Framework önceki sürümler yalnızca ve `true` değerlerini `false` destekler.

varsayılan `ContinueOnError` `ErrorAndStop` değeridir. özniteliğini olarak `ErrorAndStop` ayarsanız, davranışı proje dosyasını okuyabilen herkes için açık hale okursanız.

#### <a name="to-ignore-an-error-in-a-task"></a>Bir görev hatasını yoksaymak için

Görevin `ContinueOnError` özniteliğini kullanın. Örnek:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, hedef hala çalışır ve görev başarısız olsa bile derlemenin başarılı `Build` olduğu `Delete` kabul edilir.

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
