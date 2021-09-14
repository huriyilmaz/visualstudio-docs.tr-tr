---
title: DslTextTransform Komutu
description: DslTextTransform.cmd dosyasının TextTransform.exe çağıran ve ortak seçeneklerle çalıştıran bir betik olduğunu öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637313"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform Komutu
DslTextTransform.cmd, TextTransform.exe çağıran ve ortak seçeneklerle çalıştıran bir betiktir. Projelerinizin gecelik derlemesini otomatikleştirmek için DslTextTransformation.cmd [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] kullanabilirsiniz. Daha fazla bilgi için [bkz. TextTransform Yardımcı Programı ile Dosya Oluşturma.](../modeling/generating-files-with-the-texttransform-utility.md)

 DslTextTransform.cmd aşağıdaki dizinde bulunur:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 DslTextTransform.cmd'ye giriş olarak aşağıdaki bağımsız değişkenleri belirtsiniz:

- Etki alanı modeli projesinin çıkış dizini.

- Tasarımcı tanımı projesinin çıkış dizini.

- Metin şablonu dosyasının konumu.

  DslTextTransform.cmd, varsayılan yönerge işlemcileri ve derlemeleri kullanarak belirtilen metin şablonu dosyasını işler. Özel yönerge işlemcileri oluşturmanız, özel yönerge işlemcilerini çağıran kendi toplu iş dosyanızı TextTransform.exe. Bu toplu iş dosyasında derlemelerinizi ve ilişkili özel yönerge işlemcilerini belirtebilirsiniz.
