---
title: 'Nasıl yapılır: çağrı yığını penceresini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697484"
---
# <a name="how-to-use-the-call-stack-window"></a>Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Çağrı yığını** penceresini kullanarak, şu anda yığında olan işlev veya yordam çağrılarını görüntüleyebilirsiniz.  
  
 **Çağrı yığını** penceresi, her bir işlevin adını ve yazıldığı programlama dilini görüntüler. İşlev veya yordam adı, modül adı, satır numarası ve parametre adları, türleri ve değerleri gibi isteğe bağlı bilgiler ile birlikte olabilir. Bu isteğe bağlı bilgilerin görüntülenmesi açılabilir veya kapatılabilir.  
  
 Sarı bir ok, yürütme işaretçisinin Şu anda bulunduğu yığın çerçevesini tanımlar. Bu, varsayılan olarak, bilgileri kaynak, **ayrıştırılmış derleme**, **Yereller**, **İzle**ve **oto** pencerelerinde görünen çerçevedir. Bağlamı yığındaki başka bir çerçeveye değiştirmek istiyorsanız, bunu **çağrı yığını** penceresinde yapabilirsiniz.  
  
 Bir çağrı yığınının bir parçası için hata ayıklama sembolleri kullanılamaz olduğunda, **çağrı** yığını penceresi, çağrı yığınının o bölümü için doğru bilgileri görüntüleyemeyebilir. Aşağıdaki gösterim görünür:  
  
 [Aşağıdaki çerçeveler yanlış ve/veya eksik olabilir, name.dll için hiçbir sembol yüklenmedi]  
  
 Yönetilen kodda, varsayılan olarak. **çağrı yığını** penceresi, Kullanıcı olmayan kodun bilgilerini gizler. Gizli bilgiler yerine aşağıdaki Gösterim görünür:  
  
 **[\<External Code>]**  
  
 Kullanıcı olmayan kod, kısayol menüsünü kullanarak Kullanıcı olmayan kod için çağrı yığını bilgilerini görüntülemeyi seçebilmeniz için "My Code" olmayan bir koddur.  
  
 Kısayol menüsünü kullanarak, iş parçacıkları arasındaki çağrıları görmeyi seçebilirsiniz.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Çağrı yığını penceresini kesme modunda veya çalışma modunda görüntüleme  
  
- **Hata Ayıkla** menüsünde **Windows** ' u ve ardından **çağrı yığını**' nı seçin.  
  
### <a name="to-change-the-optional-information-displayed"></a>Görüntülenecek isteğe bağlı bilgileri değiştirmek için  
  
- **Çağrı yığını** penceresine sağ tıklayıp **göster \<**_the information that you want_**> **' i ayarlayın veya temizleyin.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Çağrı yığını penceresinde Kullanıcı olmayan kod çerçevelerini göstermek için  
  
- **Çağrı yığını** penceresine sağ tıklayın ve **dış kodu göster**' i seçin.  
  
### <a name="to-switch-to-another-stack-frame"></a>Başka bir yığın çerçevesine geçiş yapmak için  
  
1. **Çağrı yığını** penceresinde, kodunu ve verilerini görüntülemek istediğiniz çerçeveye sağ tıklayın.  
  
2. **Çerçeveye geçiş yap**' ı seçin.  
  
     Seçtiğiniz çerçevenin yanında, süslü bir kuyruklu yeşil bir ok belirir. Yürütme işaretçisi orijinal çerçevede kalır ve yine de sarı okla işaretlenir. **Hata Ayıkla** menüsünden **adımla** veya **devam et** ' i seçerseniz, yürütme, seçtiğiniz çerçeveye değil, orijinal çerçevede devam edecektir.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Başka bir iş parçacığından veya diğer bir iş parçacığından yapılan çağrıları görüntüleme  
  
- **Çağrı yığını** penceresine sağ tıklayın ve **diğer Iş parçacıklarından gelen çağrıları dahil et**' i seçin.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Çağrı yığınında bir işlevin kaynak kodunu görüntülemek için  
  
- **Çağrı yığını** penceresinde, kaynak kodunu görmek istediğiniz işlevi sağ tıklatın ve **kaynak koda git**' i seçin.  
  
### <a name="to-visually-trace-the-call-stack"></a>Çağrı yığınını görsel olarak izlemek için  
  
1. **Çağrı yığını** penceresinde, kısayol menüsünü açın. **Kod haritasında çağrı yığınını göster '** i seçin. (Klavye: **CTRL**  +  **SHIFT**  +  **`** )  
  
     [Hata ayıklama sırasında çağrı yığınında harita yöntemlerine](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)bakın.  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Çağrı yığınında bir işlevin ayrıştırılmış kodunu görüntülemek için  
  
- **Çağrı yığını** penceresinde, ayrıştırılmış derleme kodunu görmek istediğiniz işlevi sağ tıklatın ve **ayrıştırılmış koda git**' i seçin.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Çağrı yığını penceresinden belirli bir işleve çalıştırmak için  
  
- **Çağrı yığını** penceresinde, işlevi seçin, sağ tıklayın ve **imlece Çalıştır**' ı seçin.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Bir işlev çağrısının çıkış noktasında bir kesme noktası ayarlamak için  
  
- Bkz. [çağrı yığını işlevinde kesme noktası ayarlama](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Bir modülün sembollerini yüklemek için  
  
- **Çağrı yığını** penceresinde, sembolleri yeniden yüklemek istediğiniz modülün gösterildiği çerçeveye sağ tıklayın ve **sembolleri yükle**' yi seçin.  
  
## <a name="loading-symbols"></a>Semboller yükleniyor  
 **Çağrı yığını** penceresinde, şu anda yüklü sembolleri olmayan kod için hata ayıklama sembolleri yükleyebilirsiniz. Bu semboller, Microsoft ortak sembol sunucularından veya hata ayıklaması yaptığınız bilgisayardaki bir sembol yolundaki simgelerden indirilen .NET Framework veya sistem sembolleri olabilir.  
  
 Bkz [. simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Sembolleri yüklemek için  
  
1. **Çağrı yığını** penceresinde, simgelerin yüklenmediği çerçeveye sağ tıklayın. Çerçeve soluk olacak.  
  
2. **Sembolleri yükle** ' nin üzerine gelin ve ardından **Microsoft sembol sunucuları** veya **sembol yolu**' na tıklayın.  
  
#### <a name="to-set-the-symbol-path"></a>Sembol yolunu ayarlamak için  
  
1. **Çağrı yığını** penceresinde, kısayol menüsünden **sembol ayarları** ' nı seçin.  
  
     **Seçenekler** iletişim kutusu açılır ve **semboller** sayfası görüntülenir.  
  
2. **Sembol ayarları**' na tıklayın.  
  
3. **Seçenekler** Iletişim kutusunda klasör simgesine tıklayın.  
  
     **Sembol dosyası (. pdb) konumlar** kutusunda bir imleç görüntülenir.  
  
4. Hata ayıkladığınız bilgisayardaki simge konumuna bir dizin yol adı yazın. Yerel hata ayıklama için yerel bilgisayarınız budur. Uzaktan hata ayıklama için uzak bilgisayardır.  
  
5. **Seçenekler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çağrı yığını penceresinde karışık kod ve eksik bilgiler](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Nasıl yapılır: hata ayıklayıcı pencerelerinin sayısal biçimini değiştirme](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)
