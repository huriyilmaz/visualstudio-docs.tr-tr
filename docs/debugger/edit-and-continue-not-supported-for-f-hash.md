---
title: F# için Düzenle ve Devam | Microsoft Docs
description: F# hata ayıklaması için Düzenle ve Devam Etmek desteklenmiyor. Hata ayıklama sırasında kodda yapılan düzenlemeler kaynakta uygulanmaz, bu nedenle hata ayıklama yapılan kod kaynakla eşleşmez.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c37954fcb334116a81de8a29937983719f6b31ed
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725424"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Düzenle ve Devam Et F#'de Desteklenmez #
F# kodunda hata ayıklarken Düzenle ve Devam Etmek desteklenmiyor. F# kodunda düzenlemeler bir hata ayıklama oturumu sırasında mümkündür, ancak kaçınılmalıdır. Hata ayıklama oturumu sırasında kod değişiklikleri uygulanmaz. Bu nedenle, hata ayıklama sırasında F# kodunda yapılan tüm düzenlemeler, hata ayıklandırilen kodla eşleşmeen kaynak koda neden olur.
