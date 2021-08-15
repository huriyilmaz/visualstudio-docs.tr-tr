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
ms.openlocfilehash: 1c2bb7a6d4ce0304fbf0dcbf6c56778eaa189b3cd42d20f17876ae2770f1230d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316636"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform Komutu
DslTextTransform.cmd, TextTransform.exe çağıran ve ortak seçeneklerle çalıştıran bir betiktir. DslTextTransformation.cmd'i kullanarak projelerinizi gecelik derlemeyi otomatik hale [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] kullanabilirsiniz. Daha fazla bilgi için [bkz. TextTransform Yardımcı Programı ile Dosya Oluşturma.](../modeling/generating-files-with-the-texttransform-utility.md)

 DslTextTransform.cmd aşağıdaki dizinde bulunur:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 DslTextTransform.cmd'ye giriş olarak aşağıdaki bağımsız değişkenleri belirtsiniz:

- Etki alanı modeli projesinin çıkış dizini.

- Tasarımcı tanımı projesinin çıkış dizini.

- Metin şablonu dosyasının konumu.

  DslTextTransform.cmd, varsayılan yönerge işlemcileri ve derlemeleri kullanarak belirtilen metin şablonu dosyasını işler. Özel yönerge işlemcileri sanız, özel yönerge işlemcilerini çağıran kendi toplu iş TextTransform.exe. Bu toplu iş dosyasında derlemelerinizi ve ilişkili özel yönerge işlemcilerini belirtebilirsiniz.
