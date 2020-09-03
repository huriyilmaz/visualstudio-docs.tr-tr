---
title: 'Nasıl yapılır: derleme Işlemini genişletme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 789c60da5be841721ab3a999120e2fe560ffd588
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156607"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl Yapılır: Visual Studio Derleme İşlemini Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Yapı işlemi, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyanıza aktarılan bir dizi. targets dosyası tarafından tanımlanır. Bu içeri aktarılan dosyalardan biri olan Microsoft. Common. targets, derleme sürecinde birkaç noktada özel görevleri çalıştırmanıza olanak tanımak için genişletilebilir. Bu konuda, yapı işlemini genişletmek için kullanabileceğiniz iki yöntem açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

- Microsoft. Common. targets içinde tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılma.

- Microsoft. Common. targets içinde tanımlanan "Bağımlıdson" özelliklerini geçersiz kılma.

## <a name="overriding-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma
 Microsoft. Common. targets dosyası, yapı işlemindeki ana hedeflerden önce ve sonra çağrılan bir dizi önceden tanımlanmış boş hedef kümesi içerir. Örneğin, hedefi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] `BeforeBuild` ana `CoreBuild` hedeften önce ve hedeften `AfterBuild` sonra hedeften sonra çağırır `CoreBuild` . Varsayılan olarak, Microsoft. Common. targets 'daki boş hedefler hiçbir şey yapmaz, ancak Microsoft. Common. targets içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Bunu yaparak, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Yapı işlemi üzerinde size daha fazla denetim sağlamak için görevleri kullanabilirsiniz.

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz Microsoft. Common. targets içinde önceden tanımlanmış bir hedef belirler. Güvenli şekilde geçersiz kılabileceğiniz hedeflerin tamamı listesi için aşağıdaki tabloya bakın.

2. Doğrudan etiketinden önce, proje dosyanızın sonundaki hedef veya hedefleri tanımlayın `</Project>` . Örneğin:

   ```
   <Project>
       ...
       <Target Name="BeforeBuild">
           <!-- Insert tasks to run before build here -->
       </Target>
       <Target Name="AfterBuild">
           <!-- Insert tasks to run after build here -->
       </Target>
   </Project>
   ```

3. Proje dosyasını derleyin.

   Aşağıdaki tabloda, güvenli şekilde geçersiz kılabileceğiniz Microsoft. Common. targets içindeki tüm hedefler gösterilmektedir.

|Hedef Adı|Açıklama|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Bu hedeflerden birine yerleştirilen görevler, temel derlemeden önce veya sonra çalışır. Çoğu özelleştirme, bu iki hedefin birinde yapılır.|
|`BeforeBuild`, `AfterBuild`|Bu hedeflerden birine yerleştirilen görevler, derleme içindeki her şeyin öncesinde veya sonrasında çalışır. **Note:**  `BeforeBuild` Ve `AfterBuild` hedefleri, çoğu proje dosyasının sonundaki açıklamalarda zaten tanımlanmış. Bu, proje dosyanıza kolayca ve derleme sonrası olayları eklemenizi sağlar.|
|`BeforeRebuild`, `AfterRebuild`|Bu hedeflerden birine yerleştirilen görevler, temel yeniden oluşturma işlevselliği çağrılmadan önce veya sonra çalıştırılır. Microsoft. Common. targets içindeki hedef yürütmenin sırası: `BeforeRebuild` , `Clean` , `Build` , ve sonra `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Bu hedeflerden birine yerleştirilen görevler, çekirdek Temizleme işlevselliği çağrılmadan önce veya sonra çalıştırılır.|
|`BeforePublish`, `AfterPublish`|Bu hedeflerden birine yerleştirilen görevler, çekirdek yayımlama işlevselliği çağrılmadan önce veya sonra çalıştırılır.|
|`BeforeResolveReference`, `AfterResolveReferences`|Bu hedeflerden birine eklenen görevler, derleme başvuruları çözümlenmeden önce veya sonra çalıştırılır.|
|`BeforeResGen`, `AfterResGen`|Bu hedeflerden birine eklenen görevler, kaynaklar oluşturulmadan önce veya sonra çalıştırılır.|

## <a name="overriding-dependson-properties"></a>"Bağımlıdson" özelliklerini geçersiz kılma
 Önceden tanımlanmış hedefleri geçersiz kılmak, derleme işlemini genişletmenin kolay bir yoludur, ancak, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hedeflerin tanımını ardışık olarak değerlendirirken, projenizi içeri aktaran başka bir projenin, zaten geçersiz kılmış olduğunuz hedefleri geçersiz kılmasını önlemenin bir yolu yoktur. Bu nedenle, örneğin, `AfterBuild` diğer tüm projeler içeri aktarıldıktan sonra proje dosyasında tanımlanan son hedef, derleme sırasında kullanılan bir tane olur.

 `DependsOnTargets`Microsoft. Common. targets dosyasındaki özniteliklerde kullanılan "Bağımlıdson" özellikleri geçersiz kılarak, hedeflerin istenmeden geçersiz kılınmalarına karşı koruma sağlayabilirsiniz. Örneğin, hedef, `Build` `DependsOnTargets` öğesinin bir öznitelik değerini içerir `"$(BuildDependsOn)"` . Aşağıdakileri dikkate alın:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Bu XML parçası, hedefin çalıştırılabilmesi için önce `Build` özellikte belirtilen tüm hedeflerin `BuildDependsOn` önce çalıştırılması gerektiğini gösterir. `BuildDependsOn`Özelliği şu şekilde tanımlanır:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Proje dosyanızın sonunda adlı başka bir özelliği bildirerek, bu özellik değerini geçersiz kılabilirsiniz `BuildDependsOn` . Önceki `BuildDependsOn` özelliği yeni özelliğe dahil ederek, hedef listenin başına ve sonuna yeni hedefler ekleyebilirsiniz. Örneğin:

```
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

 Proje dosyalarınızı içeri aktarma projeleri, yaptığınız özelleştirmelerin üzerine yazmadan bu özellikleri geçersiz kılabilir.

#### <a name="to-override-a-dependson-property"></a>"Bağımlıdson" özelliğini geçersiz kılmak için

1. Geçersiz kılmak istediğiniz Microsoft. Common. targets içinde önceden tanımlanmış bir "Bağımlıdson" özelliği tanımla. Yaygın olarak geçersiz kılınan "Bağımlıdson" özelliklerinin listesi için aşağıdaki tabloya bakın.

2. Proje dosyanızın sonundaki özelliğin veya özelliklerin başka bir örneğini tanımlayın. Yeni özellikte, örneğin, özgün özelliğini ekleyin `$(BuildDependsOn)` .

3. Özellik tanımından önce veya sonra özel hedeflerinizi tanımlayın.

4. Proje dosyasını derleyin.

### <a name="commonly-overridden-dependson-properties"></a>Yaygın olarak "Bağımlıdson" Özellikler geçersiz kılındı

|Özellik Adı|Açıklama|
|-------------------|-----------------|
|`BuildDependsOn`|Tüm derleme işleminden önce veya sonra özel hedefler eklemek istiyorsanız geçersiz kılınacak özellik.|
|`CleanDependsOn`|Özel yapı sürecinizden çıktıyı temizlemek istiyorsanız geçersiz kılınacak özellik.|
|`CompileDependsOn`|Derleme adımından önce veya sonra özel süreçler eklemek istiyorsanız geçersiz kılınacak özellik.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md) [MSBuild kavramları](../msbuild/msbuild-concepts.md) [. Hedef dosyalar](../msbuild/msbuild-dot-targets-files.md)
