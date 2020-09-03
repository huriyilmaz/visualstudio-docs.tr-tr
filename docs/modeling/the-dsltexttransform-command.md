---
title: DslTextTransform Komutu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114909"
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
