---
title: Hata ayıklayıcısında çağrı yığınını | Microsoft Docs
description: Şu anda bir yığında bulunan işlev veya yordam çağrılarını görüntülemek için Çağrı Yığını penceresini Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e905a509443cd5fd30e860a887dd895c5ee21a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387482"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Çağrı yığınını görüntüleme ve hata ayıklayıcıda Çağrı Yığını penceresini kullanma

Çağrı Yığını **penceresini kullanarak,** o anda yığında olan işlev veya yordam çağrılarını görüntüebilirsiniz. Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yol sağlar.

Hata [ayıklama sembolleri](#bkmk_symbols) bir çağrı yığınının parçası  için kullanılamazsa, Çağrı Yığını penceresi çağrı yığınının o bölümü için doğru bilgileri görüntüleyerek bunun yerine şunları görüntüleyene kadar göstereyem olabilir:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak burada açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için Araçlar menüsünde **Ayarları İçeri ve Dışarı Aktar'ı** seçin.   Bkz. [Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="view-the-call-stack-while-in-the-debugger"></a>Hata ayıklayıcıdayken çağrı yığınını görüntüleme

- Hata ayıklama sırasında, Hata Ayıklama **menüsünde** Windows > **Çağrı Yığını'> seçin.**

  ![Çağrı Yığını Penceresi](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Sarı ok, yürütme işaretçisinin bulunduğu yığın çerçevesini tanımlar. Varsayılan olarak, bu yığın çerçevesinin bilgileri **kaynak,** **Yereller,** Otomatikler, İzleme ve Parçalara Ayır **pencerelerinde** görünür. Hata ayıklayıcı bağlamını yığında başka bir çerçeveye değiştirmek için başka [bir yığın çerçevesine geçiş.](#bkmk_switch)

## <a name="display-non-user-code-in-the-call-stack-window"></a>Çağrı Yığını penceresinde kullanıcı olmayan kodu görüntüleme

- Çağrı Yığını penceresine **sağ tıklayın ve** Dış Kodu **Göster'i seçin.**

Kullanıcı olmayan kod, kod etkinleştirildiğinde [gösterilmeyen Yalnızca kendi kodum](../debugger/just-my-code.md) koddur. Yönetilen kodda, kullanıcı olmayan kod çerçeveleri varsayılan olarak gizlenir. Aşağıdaki ifade, kullanıcı olmayan kod çerçevelerinin yerine görünür:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Başka bir yığın çerçevesine geçme (hata ayıklayıcı bağlamını değiştirme)

1. Çağrı **Yığını penceresinde,** kodunu ve verilerini görüntülemek istediğiniz yığın çerçevesine sağ tıklayın.

    Veya Çağrı Yığını penceresinde bir çerçeveye çift **tıklar** ve bu kareye geçebilirsiniz.

2. Çerçeveye **Geç'i seçin.**

     Seçtiğiniz yığın çerçevesinin yanında curly kuyruğu olan yeşil bir ok görüntülenir. Yürütme işaretçisi, hala sarı okla işaretlenmiş özgün çerçevede kalır. Hata Ayıklama **menüsünden** **Adım'ı** **veya** Devam'ı seçersiniz, yürütme seçtiğiniz çerçevede değil özgün çerçevede devam eder.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Çağrı yığınındaki bir işlevin kaynak kodunu görüntüleme

- Çağrı **Yığını penceresinde,** kaynak kodunu görmek istediğiniz işleve sağ tıklayın ve Kaynak Koda **Git'i seçin.**

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Çağrı Yığını penceresinden belirli bir işleve çalıştırma

- Çağrı **Yığını penceresinde işlevini** seçin, sağ tıklayın ve ardından İmleçte **Çalıştır'ı seçin.**

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Bir işlev çağrısının çıkış noktasında kesme noktası ayarlama

- Bkz. [Çağrı yığını işlevinde kesme noktası ayarlama.](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

## <a name="display-calls-to-or-from-another-thread"></a>Başka bir iş parçacığına veya iş parçacığından gelen çağrıları görüntüleme

- Çağrı Yığını penceresine **sağ tıklayın ve Çağrıları** Diğer İş **Parçacıklarına/İş Parçacıklarından Ekle'yi seçin.**

## <a name="visually-trace-the-call-stack"></a>Çağrı yığınını görsel olarak izleme

Bu Visual Studio Enterprise (yalnızca), hata ayıklama sırasında çağrı yığını için kod eşlemelerini görüntüebilirsiniz.

- Çağrı **Yığını penceresinde** kısayol menüsünü açın. Kod **Haritasında Çağrı Yığınını Göster 'i seçin** (**Ctrl**  +  **Shift**  +  **`** ).

    Daha fazla bilgi için hata [ayıklama sırasında çağrı yığınında eşleme yöntemlerine bakın.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

![Kod Haritasında Çağrı Yığınını Gösterme](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Çağrı yığınındaki bir işlevin disassembly kodunu görüntüleme (C#, C++, Visual Basic, F#)

- Çağrı **Yığını penceresinde,** disassembly kodunu görmek istediğiniz işleve sağ tıklayın ve **Deassembly'ye Git'i seçin.**

## <a name="change-the-optional-information-displayed"></a>Görüntülenen isteğe bağlı bilgileri değiştirme

- Çağrı Yığını penceresine sağ **tıklayın ve Göster'i** ayarlayın veya **silin. \<**_the information that you want_**>**

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Bir modül için sembolleri yükleme (C#, C++, Visual Basic, F#)

Çağrı **Yığını penceresinde,** şu anda sembolleri yüklenmemiş olan kodlar için hata ayıklama simgelerini yükleyebilirsiniz. Bu semboller Microsoft ortak sembol sunucularından indirilen .NET veya sistem sembolleri ya da hata ayıkladiğiniz bilgisayardaki bir sembol yolundaki semboller olabilir.

Bkz. [Sembol belirtme (.pdb) ve kaynak dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

### <a name="to-load-symbols"></a>Sembolleri yüklemek için

1. Çağrı **Yığını penceresinde** sembollerin yüklenmemiş olduğu yığın çerçevesine sağ tıklayın. Çerçeve soluk olur.

2. Sembolleri **Yükle'nin üzerine** gelin ve **ardından Microsoft Sembol Sunucuları'nın** (varsa) simgesini seçin veya sembol yoluna gidin.

### <a name="to-set-the-symbol-path"></a>Sembol yolunu ayarlamak için

1. Çağrı Yığını **penceresinde** kısayol **menüsünden Sembol Ayarları'ı** seçin.

     Seçenekler **iletişim** kutusu açılır ve **Semboller** sayfası görüntülenir.

2. Sembol **Ayarları'ı seçin.**

3. Seçenekler **iletişim** kutusunda Klasör simgesine tıklayın.

     Sembol **dosyası (.pdb) konumları** kutusunda bir imleç görüntülenir.

4. Hata ayıklamakta olduğunu bilgisayarda sembol konumunun bir dizin yolu adı girin. Yerel ve uzaktan hata ayıklama için bu, yerel bilgisayarınızda bir yoldur.

5. Seçenekler **iletişim** kutusunu kapatmak için **Tamam'ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı Yığını penceresinde karışık kod ve eksik bilgiler](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Kesme noktalarını kullanma](../debugger/using-breakpoints.md)