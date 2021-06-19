---
title: T4 CleanUpBehavior yönergesi
description: CleanUpBehavior yönergesi ve bir metin şablonunu işledikten sonra appDomain 'in nasıl silineceği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 078b688c238bea47e4ab38b3302708bf5e5189cf
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386351"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior yönergesi

Bir metin şablonunu işledikten sonra appDomain öğesini silmek için aşağıdaki satırı ekleyin:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Metin şablonları, ana bilgisayar işleminden ayrı bir appDomain içinde işlenir. Çoğu durumda, bir metin şablonu işlenirken, appdomain, bir sonraki şablonu işlemek için tekrar kullanılır. Ancak, CleanupBehavior belirtirseniz, appDomain silinir ve sonraki şablon yeni bir appDomain içinde işlenir.

Bu metin işlemeyi yavaşlatır, ancak kaynakların kaldırıldıklarından emin olmak için yararlı olabilir.

Bu yönerge yalnızca Visual Studio ana bilgisayarında çalışır.
