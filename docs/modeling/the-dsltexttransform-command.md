---
title: DslTextTransform Komutu
description: DslTextTransform. cmd ' nin TextTransform.exe çağıran ve bunu ortak seçeneklerle çalıştıran bir betik olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924503"
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
