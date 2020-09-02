---
title: 'Nasıl yapılır: belirli Işlevlerle Izleme sınırlandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8923323a3aed96a9dd441a4a36b2084ffd8197e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788036"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Nasıl yapılır: Belirli İşlevler için Araçları Sınırlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
    `FuncSpec` ad alanı ve işlev adıdır. Şu biçimdedir `Namespace` **::** `FunctionName` . Birden çok işlevi ayırmak için noktalı virgül kullanın. Bir \* veya daha fazla karakter için joker karakter belirtmek üzere bir yıldız işareti () kullanın. Örneğin, **/include: myNS:: \\ *** myNS ad alanındaki tüm işlevleri belirtir.  
  
   > [!NOTE]
   > Bir ikilinin işlevlerini listelemek için, Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (genellikle, yükleme dizini altındaki \Team Tools\Performance araçları dizini [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] ) ve ardından **VSInstr/DumpFuncs** yazın  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Bir ikilide belirli işlevlerle izlemeyi sınırlandırmak için  
  
1. **Performans Gezgini**' de, performans oturumunun **hedefler** düğümündeki ikili adı bulun.  
  
2. İkili adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
    **Özellik Sayfaları** iletişim kutusu görüntülenir.  
  
3. **Özellik sayfaları** Iletişim kutusunda **Gelişmiş**' e tıklayın.  
  
4. **Ek izleme seçenekleri** metin kutusunda, işaretlemek istediğiniz işlevlerin adını yazmak için aşağıdaki sözdizimini kullanın:  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`  
  
    `FuncSpec` ad alanı ve işlev adıdır. Şu biçimdedir `Namespace` **::** `FunctionName` . Birden çok işlevi ayırmak için noktalı virgül kullanın. Bir \* veya daha fazla karakter için joker karakter belirtmek üzere bir yıldız işareti () kullanın. Örneğin, **/include: myNS:: \\ *** myNS ad alanındaki tüm işlevleri belirtir.  
  
   > [!NOTE]
   > Bir ikilinin işlevlerini listelemek için, Profil Oluşturma Araçları yükleme dizininde bir komut istemi penceresi açın (genellikle, yükleme dizini altındaki \Team Tools\Performance araçları dizini [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] ) ve ardından **VSInstr/DumpFuncs** yazın  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)   
 [Nasıl yapılır: belirli dll 'Lerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Nasıl yapılır: ek Izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)
