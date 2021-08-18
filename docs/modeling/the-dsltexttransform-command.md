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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: ae937c45d0bb768bf25ef562132db136b8462805
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061174"
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
