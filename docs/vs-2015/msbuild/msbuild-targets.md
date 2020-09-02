---
title: MSBuild hedefleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4cc8d9654fc2d277f0b7c69483ab46aa3209983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157607"
---
# <a name="msbuild-targets"></a>MSBuild Hedefleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hedefleri belirli bir sırada gruplar ve derleme işleminin daha küçük birimlere ayrılabilir hale gelsin. Örneğin, bir hedef, derleme için hazırlanmak üzere çıkış dizinindeki tüm dosyaları silebilir, başka bir deyişle projenin girişlerini derler ve bunları boş dizine koyar. Görevler hakkında daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Proje dosyasındaki hedefleri bildirme  
 Hedefler, [hedef](../msbuild/target-element-msbuild.md) öğesiyle bir proje dosyasında belirtilir. Örneğin, aşağıdaki XML, derleme öğesi türü ile csc görevini çağıran bir hedef adlı bir yapı oluşturur.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 MSBuild özellikleri gibi hedefler yeniden tanımlanabilir. Örneğin,  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 AfterBuild yürütüldüğünde, yalnızca "Ikinci oluşum" görüntüler.  
  
## <a name="target-build-order"></a>Hedef Derleme Sırası  
 Bir hedefin girişi, başka bir hedefin çıktısına bağımlıysa, hedefler sıralanmalıdır. Hedeflerin çalıştırıldığı sırayı belirlemek için birkaç yol vardır.  
  
- İlk hedefler  
  
- Varsayılan hedefler  
  
- İlk hedef  
  
- Hedef bağımlılıklar  
  
- `BeforeTargets` ve `AfterTargets` (MSBuild 4,0)  
  
  Bir hedef, derleme içindeki sonraki bir hedef buna bağımlı olsa bile tek bir yapı sırasında iki kez çalıştırılmazlar. Bir hedef çalıştıktan sonra, derleme katkısı tamamlanmıştır.  
  
  Hedef derleme sırası hakkında ayrıntılar ve daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Hedef toplu Işleme  
 Hedef öğe `Outputs` ,% (Metadata) biçiminde meta verileri belirten bir özniteliğe sahip olabilir. Bu durumda, MSBuild her benzersiz meta veri değeri için hedefi bir kez çalıştırır, bu meta veri değerine sahip öğeleri gruplandırarak veya "toplu olarak" gerçekleştirir. Örneğin,  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 Başvuru öğelerini RequiredTargetFramework meta verilerine göre işler. Hedefin çıkışı şöyle görünür:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Hedef toplu işleme nadiren gerçek derlemelerde kullanılır. Görev toplu işlemi daha yaygındır. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.  
  
## <a name="incremental-builds"></a>Artımlı Derlemeler  
 Artımlı derlemeler, en iyi duruma getirilmiş derlemelerdir ve bunlara karşılık gelen giriş dosyalarına göre güncel çıkış dosyaları olan hedefler yürütülmez. Hedef öğe hem `Inputs` hem de `Outputs` özniteliğe, hedefin giriş olarak beklediği öğeleri ve çıktı olarak ürettiği öğeleri gösterir.  
  
 Tüm çıkış öğeleri güncel ise, MSBuild, derleme hızını önemli ölçüde geliştiren hedefi atlar. Bu, hedefin artımlı derlemesi olarak adlandırılır. Yalnızca bazı dosyalar güncel olduğunda, MSBuild hedefi güncel öğeler olmadan yürütür. Bu, hedefin kısmi artımlı derlemesi olarak adlandırılır. Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Nasıl Yapılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
