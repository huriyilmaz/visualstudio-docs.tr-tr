---
title: DslTextTransform Komutu
description: DslTextTransform. cmd ' nin TextTransform.exe çağıran ve bunu ortak seçeneklerle çalıştıran bir betik olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65d1e1d02c5b7d13c2e86343c6307306542d00e2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388652"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform Komutu
DslTextTransform. cmd TextTransform.exe çağıran ve bunu ortak seçeneklerle çalıştıran bir betiktir. Projelerinize yönelik gecelik bir derlemeyi otomatik hale getirmek için DslTextTransformation. cmd ' de kullanabilirsiniz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Daha fazla bilgi için bkz. [TextTransform yardımcı programıyla dosya oluşturma](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd aşağıdaki dizinde bulunur:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 DslTextTransform. cmd ' ye giriş olarak aşağıdaki bağımsız değişkenleri belirtebilirsiniz:

- Etki alanı model projesinin çıkış dizini.

- Tasarımcı tanımı projesinin çıkış dizini.

- Metin şablonu dosyasının konumu.

  DslTextTransform. cmd varsayılan yönerge işlemcileri ve derlemeleri kullanarak belirtilen metin şablonu dosyasını işler. Özel yönerge işlemcileri oluşturursanız, TextTransform.exe çağıran kendi toplu iş dosyanızı oluşturabilirsiniz. Bu toplu iş dosyasında derlemelerinizi ve ilişkili özel yönerge işlemcilerini belirtebilirsiniz.
