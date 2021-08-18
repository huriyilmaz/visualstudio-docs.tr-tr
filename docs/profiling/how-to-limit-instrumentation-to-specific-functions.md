---
title: Belirli Işlevlerle Izleme sınırlandırma | Microsoft Docs
description: Gelişmiş sayfada veya hedef ikili özellik sayfalarında seçenekleri ayarlayarak, izleme ve veri toplamayı bir veya daha fazla fonksiyona sınırlamayı öğrenin.
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
ms.openlocfilehash: 6333ea82f3b1b708561033b40ffa0cd0cdefb41f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131319"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Nasıl yapılır: belirli işlevlerle izleme sınırlandırma
**Performans oturumunun** **Gelişmiş** sayfasında veya hedef ikili özellik sayfalarında seçenekleri ayarlayarak, izleme ve veri toplamayı bir veya daha fazla fonksiyona sınırlandırabilirsiniz:

- Performans oturumu Özellik sayfasında işlevleri belirtirseniz, yalnızca bu işlevler, oturumun tüm belgelenmiş ikili dosyalarında işaretlenir.

- Hedef ikilinin Özellik sayfasında işlevleri belirtirseniz, yalnızca söz konusu ikilide olan işlevler işaretlenir. Performansın diğer ikili dosyalarında işlevleri her zamanki gibi işaretlenir.

  Veri toplamayı bu şekilde sınırlandırma yalnızca, izleme profili oluşturma yöntemi seçildiğinde desteklenir.

> [!NOTE]
> Ayrıca, Profil Oluşturma Araçları [vsinstr](../profiling/vsinstr.md) komut satırı araç aracı tarafından kullanılabilen diğer seçenekleri ayarlamak Için **performans oturumu** özellik sayfalarının **Gelişmiş** sayfasını da kullanabilirsiniz.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Bir performans oturumunda belirli işlevlere yönelik izleme sınırlandırmak için

1. **Performans Gezgini**, oturum adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

    **Özellik Sayfaları** iletişim kutusu görüntülenir.

2. **Özellik sayfaları** Iletişim kutusunda **Gelişmiş**' e tıklayın.

3. **Ek izleme seçenekleri** metin kutusunda, işaretlemek istediğiniz işlevlerin adını yazmak için aşağıdaki sözdizimini kullanın:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` ad alanı ve işlev adıdır. Şu biçimdedir `Namespace` **::** `FunctionName` . Birden çok işlevi ayırmak için noktalı virgül kullanın. Bir \* veya daha fazla karakter için joker karakter belirtmek üzere bir yıldız işareti () kullanın. Örneğin, **/include: myNS:: \\*** myNS ad alanındaki tüm işlevleri belirtir.

   > [!NOTE]
   > Bir ikilinin işlevlerini listelemek için, Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (bkz [. komut satırı araçlarının yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) ve ardından **VSInstr/DumpFuncs** yazın

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Bir ikilide belirli işlevlerle izlemeyi sınırlandırmak için

1. **Performans Gezgini**' de, performans oturumunun **hedefler** düğümündeki ikili adı bulun.

2. İkili adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

    **Özellik Sayfaları** iletişim kutusu görüntülenir.

3. **Özellik sayfaları** Iletişim kutusunda **Gelişmiş**' e tıklayın.

4. **Ek izleme seçenekleri** metin kutusunda, işaretlemek istediğiniz işlevlerin adını yazmak için aşağıdaki sözdizimini kullanın:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec` ad alanı ve işlev adıdır. Şu biçimdedir `Namespace` **::** `FunctionName` . Birden çok işlevi ayırmak için noktalı virgül kullanın. Bir \* veya daha fazla karakter için joker karakter belirtmek üzere bir yıldız işareti () kullanın. Örneğin, **/include: myNS:: \\*** myNS ad alanındaki tüm işlevleri belirtir.

   > [!NOTE]
   > Bir ikilinin işlevlerini listelemek için, Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (bkz [. komut satırı araçlarının yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) ve ardından **VSInstr/DumpFuncs** yazın

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Nasıl yapılır: İzlemeyi belirli DLL'ler ile sınırlama](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)
