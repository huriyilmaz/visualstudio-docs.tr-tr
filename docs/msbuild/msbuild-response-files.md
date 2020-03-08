---
title: MSBuild yanıt dosyaları | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410039"
---
# <a name="msbuild-response-files"></a>MSBuild yanıt dosyaları

Yanıt ( *. rsp*) dosyaları, *MSBuild. exe* komut satırı anahtarlarını içeren metin dosyalarıdır. Her anahtar ayrı bir satırda olabilir veya tüm anahtarlar tek bir satırda olabilir. Açıklama satırları **#** simgesiyle önceden başlar. **@** anahtarı, *MSBuild. exe*' ye başka bir yanıt dosyası geçirmek için kullanılır.

## <a name="msbuildrsp"></a>MSBuild. rsp

Otomatik yanıt dosyası, *MSBuild. exe* ' nin bir proje oluştururken otomatik olarak kullandığı özel bir *. rsp* dosyasıdır. Bu dosya, *MSBuild. rsp*, *MSBuild. exe*ile aynı dizinde olmalıdır, aksi halde bulunamamıştır. Bu dosyayı, *MSBuild. exe*için varsayılan komut satırı anahtarlarını belirtmek üzere düzenleyebilirsiniz. Örneğin, her proje oluşturduğunuzda aynı günlükçü kullanırsanız, *MSBuild. rsp*dosyasına **-günlükçü** anahtarını ekleyebilirsiniz ve *MSBuild. exe* , bir proje oluşturulduğunda günlükçü 'yi kullanır.

## <a name="directorybuildrsp"></a>Directory. Build. rsp

Sürüm 15,6 ve üzeri sürümlerde MSBuild, *Directory. Build. rsp*adlı bir dosya için projenin üst dizinlerini arayacak.  Bu, komut satırı derlemeleri sırasında varsayılan bağımsız değişkenler sağlamak için bir kaynak kod deposunda yararlı olabilir.  Barındırılan yapıların komut satırı bağımsız değişkenlerini belirtmek için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
