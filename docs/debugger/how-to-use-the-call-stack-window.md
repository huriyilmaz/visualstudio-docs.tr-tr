---
title: Hata ayıklayıcıda çağrı yığınını görüntüle | Microsoft Docs
description: Şu anda Visual Studio 'daki yığında olan işlev veya yordam çağrılarını görüntülemek için çağrı yığını penceresini kullanın.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/29/2018
ms.topic: how-to
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 206c79a47ec59e02206332d80d1afe935fb72bdc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150632"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Çağrı yığınını görüntüleyin ve hata ayıklayıcıda çağrı yığını penceresini kullanın

**Çağrı yığını** penceresini kullanarak, şu anda yığında olan işlev veya yordam çağrılarını görüntüleyebilirsiniz. Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

[Hata ayıklama sembolleri](#bkmk_symbols) bir çağrı yığınının bir parçası için kullanılabilir olmadığında, **çağrı yığını** penceresi, çağrı yığınının bu bölümü için doğru bilgileri görüntüleyemeyebilir, bunun yerine şunu görüntüleyebilirsiniz:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak burada açıklananlardan farklı bir şekilde farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin.  Bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Hata ayıklayıcı sırasında çağrı yığınını görüntüle

- Hata ayıklama sırasında, **hata ayıklama** menüsünde **Windows > çağrı yığını**' nı seçin.

  ![Çağrı yığını penceresi](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Sarı bir ok, yürütme işaretçisinin Şu anda bulunduğu yığın çerçevesini tanımlar. Varsayılan olarak, bu yığın çerçevesinin bilgileri kaynak, **Yereller**, **oto**'Ler, **İzle** ve **ayrıştırma** pencerelerinde görüntülenir. Hata ayıklayıcı bağlamını yığındaki başka bir çerçeveye değiştirmek için [başka bir yığın çerçevesine geçin](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Çağrı yığını penceresinde Kullanıcı olmayan kodu görüntüle

- **Çağrı yığını** penceresine sağ tıklayın ve **dış kodu göster**' i seçin.

Kullanıcı dışı kod, [yalnızca kendi kodum](../debugger/just-my-code.md) etkinleştirildiğinde gösterilmeyen bir koddur. Yönetilen kodda, Kullanıcı olmayan kod çerçeveleri varsayılan olarak gizlidir. Kullanıcı dışı kod çerçevelerinin yerine aşağıdaki Gösterim görünür:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Başka bir yığın çerçevesine geç (hata ayıklayıcı bağlamını değiştirin)

1. **Çağrı yığını** penceresinde, kod ve verilerini görüntülemek istediğiniz yığın çerçevesine sağ tıklayın.

    Ya da bu çerçeveye geçiş yapmak için **çağrı yığını** penceresinde bir çerçeveye çift tıklayabilirsiniz.

2. **Çerçeveye geçiş yap**' ı seçin.

     Seçtiğiniz yığın çerçevesinin yanında, süslü bir kuyruklu yeşil bir ok belirir. Yürütme işaretçisi orijinal çerçevede kalır ve yine de sarı okla işaretlenir. **Hata Ayıkla** menüsünden **adımla** veya **devam et** ' i seçerseniz, yürütme, seçtiğiniz çerçeveye değil, orijinal çerçevede devam edecektir.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Çağrı yığınında bir işlevin kaynak kodunu görüntüleme

- **Çağrı yığını** penceresinde, kaynak kodunu görmek istediğiniz işlevi sağ tıklatın ve **kaynak koda git**' i seçin.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Çağrı yığını penceresinden belirli bir işleve Çalıştır

- **Çağrı yığını** penceresinde, işlevi seçin, sağ tıklayın ve ardından **imlece Çalıştır**' ı seçin.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>İşlev çağrısının çıkış noktasında bir kesme noktası ayarlayın

- Bkz. [çağrı yığını işlevinde kesme noktası ayarlama](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Başka bir iş parçacığından veya bir iş parçacığından yapılan çağrıları görüntüle

- **Çağrı yığını** penceresine sağ tıklayın ve **diğer Iş parçacıklarından gelen çağrıları dahil et**' i seçin.

## <a name="visually-trace-the-call-stack"></a>Çağrı yığınını görsel olarak izleme

Visual Studio Enterprise (yalnızca) ' de, hata ayıklarken çağrı yığını için kod eşlemelerini görüntüleyebilirsiniz.

- **Çağrı yığını** penceresinde, kısayol menüsünü açın. **Kod haritasında çağrı yığınını göster** (**CTRL**  +  **SHIFT**) seçeneğini belirleyin  +  **`** .

    Daha fazla bilgi için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Kod haritasında çağrı yığınını göster](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Çağrı yığınında bir işlevin ayrıştırılmış kodunu görüntüleme (C#, C++, Visual Basic, F #)

- **Çağrı yığını** penceresinde, ayrıştırılmış derleme kodunu görmek istediğiniz işlevi sağ tıklatın ve **ayrıştırılmış koda git**' i seçin.

## <a name="change-the-optional-information-displayed"></a>Gösterildiği isteğe bağlı bilgileri değiştirme

- **Çağrı yığını** penceresine sağ tıklayıp **göster \<**_the information that you want_**>**' i ayarlayın veya temizleyin.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Modül için yükleme sembolleri (C#, C++, Visual Basic, F #)

**Çağrı yığını** penceresinde, şu anda yüklü sembolleri olmayan kod için hata ayıklama sembolleri yükleyebilirsiniz. Bu semboller .NET veya Microsoft ortak sembol sunucularından indirilen sistem sembolleri veya hata ayıkladığınız bilgisayardaki bir sembol yolundaki semboller olabilir.

Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Sembolleri yüklemek için

1. **Çağrı yığını** penceresinde, simgelerin yüklenmediği yığın çerçevesini sağ tıklatın. Çerçeve soluk olacak.

2. **Sembolleri yükle** ' nin üzerine gelin ve ardından **Microsoft sembol sunucularını** (varsa) seçin veya sembol yoluna gidin.

### <a name="to-set-the-symbol-path"></a>Sembol yolunu ayarlamak için

1. **Çağrı yığını** penceresinde, kısayol menüsünden **sembol ayarları** ' nı seçin.

     **Seçenekler** iletişim kutusu açılır ve **semboller** sayfası görüntülenir.

2. **Sembol ayarları**' nı seçin.

3. **Seçenekler** Iletişim kutusunda klasör simgesine tıklayın.

     **Sembol dosyası (. pdb) konumlar** kutusunda bir imleç görüntülenir.

4. Hata ayıkladığınız bilgisayardaki simge konumuna bir dizin yol adı girin. Yerel ve uzaktan hata ayıklama için bu, yerel bilgisayarınızdaki bir yoldur.

5. **Seçenekler** iletişim kutusunu kapatmak için **Tamam ' ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı Yığını penceresinde karışık kod ve eksik bilgiler](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Kesme noktalarını kullanma](../debugger/using-breakpoints.md)