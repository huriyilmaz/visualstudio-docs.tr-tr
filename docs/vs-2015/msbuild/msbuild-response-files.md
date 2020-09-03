---
title: MSBuild yanıt dosyaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189370"
---
# <a name="msbuild-response-files"></a>MSBuild Yanıt Dosyaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yanıt (. rsp) dosyaları MSBuild.exe komut satırı anahtarları içeren metin dosyalarıdır. Her anahtar ayrı bir satırda olabilir veya tüm anahtarlar tek bir satırda olabilir. Açıklama satırları bir sembol ile önceden başlar **#** . **@** Anahtar, MSBuild.exe başka bir yanıt dosyası geçirmek için kullanılır.  
  
 Otomatik yanıt dosyası, MSBuild.exe otomatik olarak bir proje oluştururken kullanılan özel bir. rsp dosyasıdır. Bu dosya, MSBuild. rsp, MSBuild.exe ile aynı dizinde olmalıdır, aksi halde bulunamacaktır. Bu dosyayı, MSBuild.exe için varsayılan komut satırı anahtarlarını belirtmek üzere düzenleyebilirsiniz. Örneğin, bir proje oluşturduğunuzda aynı günlükçüsü kullanırsanız, **/günlükçü** anahtarını MSBuild. rsp ' ye ekleyebilirsiniz ve MSBuild.exe bir proje oluşturulduğunda günlükçü kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
