---
title: Ölçüm ölçümlerini Belirli İşlevler ile | Microsoft Docs
description: Gelişmiş sayfasında veya hedef ikili özellik sayfalarında seçenekleri ayarerek ölçüm ve veri toplamayı bir veya daha fazla işlevle sınırlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 23924193840226117c6e63541f8288faf8962be2781d634b1040964f3202571f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396493"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Nasıl kullanılır: Araçları belirli işlevlerle sınırlama
Performans Oturumu'nın Gelişmiş sayfasındaki seçenekleri veya hedef ikili  özellik sayfalarını ayarerek ölçüm ve veri toplamayı bir **veya** daha fazla işlevle sınırleyebilirsiniz:

- İşlevleri performans oturumu özellik sayfasında belirtirsiniz, oturumun tüm araçlı ikili dosyalarında yalnızca bu işlevler görüntülenir.

- İşlevleri bir hedef ikilinin özellik sayfasında belirtirsiniz, yalnızca ilgili ikili dosyada yer alan işlevler takip eder. Performansın diğer ikililerinde yer alan işlevler her zamanki gibi takip eder.

  Veri toplamayı bu şekilde sınırlamak yalnızca ölçümleme profil oluşturma yöntemi seçildiğinde de kullanılabilir.

> [!NOTE]
> [VsInstr](../profiling/vsinstr.md) komut **satırı** araçları  için kullanılabilen diğer seçenekleri ayarlamak için Performans Oturumu özellik sayfalarının Gelişmiş sayfasını da Profil Oluşturma Araçları kullanabilirsiniz.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Bir performans oturumunda araçları belirli işlevlerle sınırlamak için

1. Bu **Performans Gezgini** oturum adına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

    **Özellik Sayfaları** iletişim kutusu görüntülenir.

2. Özellik Sayfaları **iletişim kutusunda** Gelişmiş'e **tıklayın.**

3. Ek **ölçüm seçenekleri metin** kutusunda, takip etmek istediğiniz işlevlerin adını yazarak aşağıdaki söz dizimlerini kullanın:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` ad alanı ve işlev adıdır. Şu biçime `Namespace` **sahip:** `FunctionName` . Birden çok işlevi ayırmak için noktalı virgül kullanın. Bir veya daha fazla karakter için joker karakter belirtmek üzere yıldız işareti ( \* ) kullanın. Örneğin, **/include:MyNS:: \\*** MyNS ad alanının tüm işlevlerini belirtir.

   > [!NOTE]
   > İkili dosyada işlevleri listeleyebilirsiniz, Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (bkz. Komut satırı araçlarının yolunu [belirtme)](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)ve **ardından vsinstr /DumpFuncs yazın**

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Araçları bir ikili dosyada belirli işlevlerle sınırlamak için

1. Bu **Performans Gezgini,** performans oturumunun Hedefler **düğümünde** ikili adı bulun.

2. İkili adına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

    **Özellik Sayfaları** iletişim kutusu görüntülenir.

3. Özellik Sayfaları **iletişim kutusunda** Gelişmiş'e **tıklayın.**

4. Ek **ölçüm seçenekleri metin** kutusunda, takip etmek istediğiniz işlevlerin adını yazarak aşağıdaki söz dizimlerini kullanın:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` ad alanı ve işlev adıdır. Şu biçime `Namespace` **sahip:** `FunctionName` . Birden çok işlevi ayırmak için noktalı virgül kullanın. Bir veya daha fazla karakter için joker karakter belirtmek üzere yıldız işareti ( \* ) kullanın. Örneğin, **/include:MyNS:: \\*** MyNS ad alanının tüm işlevlerini belirtir.

   > [!NOTE]
   > İkili dosyada işlevleri listeleyebilirsiniz, Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (bkz. Komut satırı araçlarının yolunu [belirtme)](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)ve **ardından vsinstr /DumpFuncs yazın**

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Nasıl yapılır: İzlemeyi belirli DLL'ler ile sınırlama](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)
