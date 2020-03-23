---
title: 'Nasıl Yapılır: Enstrümantasyonu Belirli İşlevler ile Sınırlandırın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 34a63645933a173e449cf4292cc3d014cc3ec740
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775325"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Nasıl yapılır: Enstrümantasyonu belirli işlevler ile sınırlandırın
**Performans Oturumu'nun** **Gelişmiş** sayfasında seçenekleri ayarlayarak veya ikili özellik sayfalarını hedefleyerek enstrümantasyon ve veri toplamayı bir veya daha fazla işleyle sınırlandırabilirsiniz:

- Performans oturumu özelliği sayfasındaki işlevleri belirtirseniz, yalnızca bu işlevler oturumun tüm enstrümanted ikililerinde işletilir.

- Hedef ikilinin özellik sayfasındaki işlevleri belirtirseniz, yalnızca o ikilideki işlevler işletilir. Performansın diğer ikili işlevleri her zamanki gibi enstrümantedir.

  Veri toplamayı bu şekilde sınırlamak, yalnızca enstrümantasyon profil oluşturma yöntemi seçildiğinde desteklenir.

> [!NOTE]
> Profil Oluşturma Araçları [VSInstr](../profiling/vsinstr.md) komut satırı enstrümantasyon aracıiçin kullanılabilen diğer seçenekleri ayarlamak için **Performans Oturumu** özellik sayfalarının **Gelişmiş** sayfasını da kullanabilirsiniz.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Enstrümantasyonu bir performans oturumundaki belirli işlevler ile sınırlamak için

1. **Performans Gezgini'nde,** oturum adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

    **Özellik Sayfaları** iletişim kutusu görüntülenir.

2. Özellik **Sayfaları** iletişim kutusunda **Gelişmiş'i**tıklatın.

3. Ek **enstrümantasyon seçenekleri** metin kutusunda, enstrüman istediğiniz işlevlerin adını yazmak için aşağıdaki sözdizimini kullanın:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec`ad alanı ve işlev adıdır. Bu biçimi `Namespace`vardır **::**`FunctionName`. Birden çok işlevi ayırmak için bir yarı nokta kullanın. Bir veya daha\*fazla karakter için joker karakter belirtmek için yıldız işareti () kullanın. Örneğin, **/include:MyNS::\\*** MyNS ad alanında tüm işlevleri belirtir.

   > [!NOTE]
   > İkili işlevleri listelemek için Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (bkz. [komut satırı araçlarına giden yolu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) ve ardından **vsinstr /DumpFuncs** yazın

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Enstrümantasyonu ikili bir fonksiyondaki belirli işlevler ile sınırlamak için

1. **Performans Gezgini'nde,** performans oturumunun **Hedef** düğümünde ikili adı bulun.

2. İkili adı sağ tıklatın ve sonra **Özellikler'i**tıklatın.

    **Özellik Sayfaları** iletişim kutusu görüntülenir.

3. Özellik **Sayfaları** iletişim kutusunda **Gelişmiş'i**tıklatın.

4. Ek **enstrümantasyon seçenekleri** metin kutusunda, enstrüman istediğiniz işlevlerin adını yazmak için aşağıdaki sözdizimini kullanın:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec`ad alanı ve işlev adıdır. Bu biçimi `Namespace`vardır **::**`FunctionName`. Birden çok işlevi ayırmak için bir yarı nokta kullanın. Bir veya daha\*fazla karakter için joker karakter belirtmek için yıldız işareti () kullanın. Örneğin, **/include:MyNS::\\*** MyNS ad alanında tüm işlevleri belirtir.

   > [!NOTE]
   > İkili işlevleri listelemek için Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (bkz. [komut satırı araçlarına giden yolu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)) ve ardından **vsinstr /DumpFuncs** yazın

## <a name="see-also"></a>Ayrıca bkz.
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
- [Nasıl yapılır: İzlemeyi belirli DLL'ler ile sınırlama](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)
