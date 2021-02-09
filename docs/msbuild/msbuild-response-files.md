---
title: MSBuild yanıt dosyaları | Microsoft Docs
description: MSBuild yanıtı veya. rsp dosyaları, MSBuild.exe komut satırı anahtarları içeren metin dosyaları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17a4e10864776540c176fd6911917071aa42c656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860873"
---
# <a name="msbuild-response-files"></a>MSBuild yanıt dosyaları

Yanıt (*. rsp*) dosyaları *MSBuild.exe* komut satırı anahtarları içeren metin dosyalarıdır. Her anahtar ayrı bir satırda olabilir veya tüm anahtarlar tek bir satırda olabilir. Açıklama satırları bir sembol ile önceden başlar **#** . **@** Anahtar, *MSBuild.exe* başka bir yanıt dosyası geçirmek için kullanılır.

## <a name="msbuildrsp"></a>MSBuild. rsp

Otomatik yanıt dosyası, *MSBuild.exe* otomatik olarak bir proje oluştururken kullanılan özel bir *. rsp* dosyasıdır. Bu dosya, *MSBuild. rsp*, *MSBuild.exe* ile aynı dizinde olmalıdır, aksi halde bulunamacaktır. Bu dosyayı, *MSBuild.exe* için varsayılan komut satırı anahtarlarını belirtmek üzere düzenleyebilirsiniz. Örneğin, her proje oluşturduğunuzda aynı günlükçü kullanırsanız, *MSBuild. rsp*' ye **-günlükçü** anahtarını ekleyebilirsiniz ve *MSBuild.exe* bir proje oluşturulduğunda günlükçü kullanılır.

## <a name="directorybuildrsp"></a>Directory. Build. rsp

Sürüm 15,6 ve üzeri sürümlerde MSBuild, *Directory. Build. rsp* adlı bir dosya için projenin üst dizinlerini arayacak.  Bu, komut satırı derlemeleri sırasında varsayılan bağımsız değişkenler sağlamak için bir kaynak kod deposunda yararlı olabilir.  Barındırılan yapıların komut satırı bağımsız değişkenlerini belirtmek için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
