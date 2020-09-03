---
title: DslTextTransform komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658459"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform Komutu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd TextTransform.exe çağıran ve bunu ortak seçeneklerle çalıştıran bir betiktir. Projelerinize yönelik gecelik bir derlemeyi otomatik hale getirmek için DslTextTransformation. cmd ' de kullanabilirsiniz [!INCLUDE[dsl](../includes/dsl-md.md)] . Daha fazla bilgi için bkz. [TextTransform yardımcı programıyla dosya oluşturma](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd aşağıdaki dizinde bulunur:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 DslTextTransform. cmd ' ye giriş olarak aşağıdaki bağımsız değişkenleri belirtebilirsiniz:

- Etki alanı model projesinin çıkış dizini.

- Tasarımcı tanımı projesinin çıkış dizini.

- Metin şablonu dosyasının konumu.

  DslTextTransform. cmd varsayılan yönerge işlemcileri ve derlemeleri kullanarak belirtilen metin şablonu dosyasını işler. Özel yönerge işlemcileri oluşturursanız, TextTransform.exe çağıran kendi toplu iş dosyanızı oluşturabilirsiniz. Bu toplu iş dosyasında derlemelerinizi ve ilişkili özel yönerge işlemcilerini belirtebilirsiniz.
