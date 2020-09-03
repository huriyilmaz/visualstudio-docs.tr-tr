---
title: Kaçış için özel karakterler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161350"
---
# <a name="special-characters-to-escape"></a>Kaçış İçin Özel Karakterler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel karakterler yalnızca kullanıldıkları bağlamda özel anlam içeriyorsa kaçışmalıdır. Örneğin, yıldız işareti (*) yalnızca bir öğe tanımının "Içerme" ve "hariç tutma" özniteliklerinde ya da öğesine yapılan çağrıda özel bir karakterdir <xref:Microsoft.Build.Tasks.CreateItem> . Diğer tüm durumlarda, yıldız işareti sabit bir yıldız işareti olarak değerlendirilir. Proje dosyalarında herhangi bir yerde yıldız işaretleri gerekmez, ancak bunu yapmak zarar vermez.  
  
 Özel karakterin yerine%*xx* gösterimini kullanın; burada *xx* , ASCII karakterinin onaltılı değerini temsil eder. Örneğin, bir yıldız işareti (*) sabit karakter olarak kullanmak için değerini kullanın `%2A` .  
  
 Kaçış için özel karakterlerin tam listesi aşağıdadır:  
  
|Karakter|Açıklama|  
|---------------|-----------------|  
|%|Meta verilere başvurmak için kullanılan yüzde işareti.|  
|$|Dolar işareti, özelliklere başvurmak için kullanılır.|  
|@|Öğesinde, öğe listelerine başvurmak için kullanılır.|  
|(|Listelerde kullanılan parantez açın.|  
|)|Listelerde kullanılan parantez kapatma.|  
|`|Koşullarda ve diğer ifadelerde kullanılan kesme işareti (veya değer çizgisi).|  
|;|Noktalı virgül, liste ayırıcısı.|  
|?|Soru işareti, bir öğenin Içerme/hariç tutma bölümünde bir dosya belirtimini açıklayan bir joker karakterdir.|  
|*|Bir öğenin Içerme/hariç tutma bölümünde bir dosya belirtimini açıklayan bir joker karakter olan yıldız işareti.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: MSBuild 'de özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)
