---
title: Artımlı derlemeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb11467d8d59e7af11741d7719da2858ac1a784c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192888"
---
# <a name="incremental-builds"></a>Artımlı Derlemeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Artımlı derlemeler, en iyileştirilmiş derlemelerdir, böylece ilgili giriş dosyalarına göre güncel çıkış dosyaları olan hedefler yürütülmez. Hedef öğe, her iki özniteliğe de sahip olabilir, bu da `Inputs` hedefin girdi olarak beklediği öğeleri ve bir `Outputs` özniteliği, çıktı olarak ürettiği öğeleri gösterir. MSBuild, bu özniteliklerin değerleri arasında 1 ila 1 eşleme bulmaya çalışır. 1-1 eşleme varsa, MSBuild her giriş öğesinin zaman damgasını karşılık gelen çıkış öğesinin zaman damgasıyla karşılaştırır. 1--1 eşleştirmesi olmayan çıkış dosyaları tüm giriş dosyalarıyla karşılaştırılır. Çıkış dosyası, giriş dosyası veya dosyalarından aynı yaş veya daha yeniyse bir öğe güncel olarak değerlendirilir.  
  
 Tüm çıkış öğeleri güncel ise, MSBuild hedefi atlar. Hedefin bu *artımlı derlemesi* , derleme hızını önemli ölçüde iyileştirebilir. Yalnızca bazı dosyalar güncel ise, MSBuild hedefi yürütür, ancak güncellik öğelerini atlar ve böylece tüm öğeleri güncel hale getirir. Bu *kısmi Artımlı derleme*olarak bilinir.  
  
 1--1 eşlemeleri genellikle öğe dönüştürmeleri tarafından üretilir. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).  
  
 Aşağıdaki hedefi göz önünde bulundurun.  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Öğe türü tarafından temsil edilen dosya kümesi `Compile` bir yedekleme dizinine kopyalanır. Yedekleme dosyaları. bak dosya adı uzantısına sahiptir. Öğe türü tarafından temsil edilen dosyalar `Compile` veya buna karşılık gelen yedekleme dosyaları, yedekleme hedefi çalıştıktan sonra silinmez veya değiştirilmez, sonraki derlemelerde yedekleme hedefi atlanır.  
  
## <a name="output-inference"></a>Çıkış çıkarımı  
 MSBuild, hedefin `Inputs` `Outputs` yürütülüp yürütülmeyeceğini tespit etmek için bir hedefin ve özniteliklerini karşılaştırır. İdeal olarak, bir artımlı derleme tamamlandıktan sonra var olan dosyalar kümesi, ilişkili hedeflerin yürütülüp yürütülmediği gibi aynı kalacaktır. Görevler tarafından oluşturulan veya değiştirilen özellikler ve öğeler derlemeyi etkileyebildiğinden, bunları etkileyen hedef atlansa bile MSBuild, değerlerini çıkarmalıdır. Bu, *Çıkış çıkarımı*olarak bilinir.  
  
 Üç durum vardır:  
  
- Hedefte `Condition` değerlendirilen bir özniteliği vardır `false` . Bu durumda, hedef çalıştırılmaz ve derleme üzerinde hiçbir etkisi yoktur.  
  
- Hedefte güncel olmayan çıkışlar vardır ve bunları güncel hale getirmek için çalıştırılır.  
  
- Hedefte güncel olmayan çıkışlar yok ve atlandı. MSBuild hedefi değerlendirir ve hedef çalıştırılmışsınız gibi öğe ve özelliklerde değişiklikler yapar.  
  
  Artımlı derlemeyi desteklemek için, görevler `TaskParameter` herhangi `Output` bir öğenin öznitelik değerinin bir görev giriş parametresine eşit olduğundan emin olmalıdır. İşte bazı örnekler:  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Bu özellik, hedefin yürütülüp yürütülmediğini veya atlanmadığını "123" değerine sahip kolay bir şekilde oluşturur.  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Bu, "a.cs" ve "b.cs" olmak üzere iki öğeye sahip basit öğe türü oluşturur, çünkü hedefin yürütülüp yürütülmeyeceğini veya atlanıp atlanmadığını belirtir.  
  
 MSBuild 3,5 ' den başlayarak, bir hedefteki öğe ve özellik grupları üzerinde çıkış çıkarımı otomatik olarak gerçekleştirilir. `CreateItem` görevler bir hedefte gerekli değildir ve kaçınılmalıdır. Ayrıca, `CreateProperty` Görevler bir hedefte yalnızca bir hedefin yürütülüp yürütülmediğini anlamak için kullanılmalıdır.  
  
## <a name="determining-whether-a-target-has-been-run"></a>Bir hedefin çalıştırılıp çalıştırılmadığını belirleme  
 Çıkış çıkarımı nedeniyle, `CreateProperty` hedefin yürütülüp yürütülmediğini belirleyebilmeniz için özellikleri ve öğeleri incelemek üzere bir hedefe görev eklemeniz gerekir. `CreateProperty`Görevi hedefe ekleyin ve `Output` `TaskParameter` "ValueSetByTask" olan bir öğe verin.  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Bu, Compilera özelliğini oluşturur ve `true` yalnızca hedef yürütülürse değeri verir. Hedef atlandıysa, Compilera oluşturulmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Targets](../msbuild/msbuild-targets.md)
