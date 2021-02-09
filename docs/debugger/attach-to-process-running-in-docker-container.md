---
title: Docker kapsayıcısında çalışan bir işleme iliştirme
description: Visual Studio kullanarak Docker kapsayıcısı çalıştıran bir uygulamada hata ayıklamayı öğrenin
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 4f39d4ecd69b726c1d549d723fadd324b1edd722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857935"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Docker kapsayıcısında çalışan bir işleme iliştirme 

Visual Studio 'Yu kullanarak bir Windows Docker kapsayıcısında veya Linux .NET Core Docker kapsayıcısında çalışan uygulamalarda hata ayıklaması yapabilirsiniz.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Linux Docker kapsayıcısında çalışan bir işleme iliştirme

Visual Studio hata ayıklayıcısını, **Işleme Ekle** iletişim kutusunu kullanarak yerel veya uzak makinenizde Linux .NET Core Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için .NET Core platformlar arası geliştirme iş yükünü yüklemeli ve kaynak koda yerel erişim sahibi olmanız gerekir.

**Linux Docker kapsayıcısında çalışan bir işleme iliştirmek için:**

1. Visual Studio 'da, işleme **Ekle** iletişim kutusunu açmak Için **Hata Ayıkla > Işleme Ekle (Ctrl + Alt + P)** öğesini seçin.

![Visual Studio 'da Işleme Iliştir iletişim kutusunun ekran görüntüsü (Linux kapsayıcısı) bir bağlantı türünü gösterir.](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. **Bağlantı türünü** **Docker (Linux kapsayıcısı)** olarak ayarlayın.
3. **Docker kapsayıcısını Seç** iletişim kutusunu kullanarak **bağlantı hedefini** ayarlamak için **bul...** seçeneğini belirleyin.

    Bir Docker kapsayıcı işleminde yerel olarak veya uzaktan hata ayıklaması yapabilirsiniz.

    **Bir Docker kapsayıcı işleminde yerel olarak hata ayıklamak için:**
    1. **Docker CLI ana bilgisayarını** **yerel makineye** ayarlayın.
    1. Listeden eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a** basın.

    ![Docker kapsayıcı menüsünü seçin](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **Kenarı. Bir Docker kapsayıcı işleminde uzaktan hata ayıklamak için:**

    > [!NOTE]
    > Bir Docker kapsayıcısında çalışan bir işleme uzaktan bağlanmak için iki seçenek vardır. SSH 'yi kullanmak için ilk seçenek, yerel makinenizde Docker Araçları yüklü değilse idealdir.  Yerel olarak Docker Araçları yüklüyse ve uzak istekleri kabul edecek şekilde yapılandırılmış bir Docker Daemon varsa, bir Docker Daemon kullanarak ikinci seçeneği deneyin.

    1. ***SSH aracılığıyla uzak makineye bağlanmak için:***
        1. Uzak bir sisteme bağlanmak için **Ekle...** öğesini seçin.<br/>
        ![Uzak bir sisteme bağlanma](../debugger/media/connect-remote-system.png "Uzak bir sisteme bağlanma")
        1. SSH veya Daemon 'e başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a** basın.

    1. ***Hedefi bir [Docker Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla bir işlem çalıştıran uzak kapsayıcıya ayarlamak için***
        1. **Docker Konağı (Isteğe bağlı)** altında, Daemon ADRESINI (TCP, IP vb.) belirtin ve Yenile bağlantısına tıklayın.
        1. Daemon 'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a** basın.

4. **Kullanılabilir işlemler** listesinden karşılık gelen kapsayıcı işlemini seçin ve Visual Studio 'Da C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin!

    ![Visual Studio 'da Işleme Iliştir iletişim kutusunun ekran görüntüsü. Bağlantı türü Docker (Linux kapsayıcısı) olarak ayarlanır ve DotNet işlemi seçilidir.](../debugger/media/docker-attach-complete.png "Tamamlanmış Linux Docker Iliştirme menüsü")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Windows Docker kapsayıcısında çalışan bir işleme iliştirme

Visual Studio hata ayıklayıcısını, **Işleme Ekle** iletişim kutusunu kullanarak yerel makinenizde bir Windows Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz.

> [!IMPORTANT]
> Bu özelliği bir .NET Core işlemiyle birlikte kullanmak için .NET Core platformlar arası geliştirme iş yükünü yüklemeli ve kaynak koda yerel erişim sahibi olmanız gerekir.

**Bir Windows Docker kapsayıcısında çalışan bir işleme iliştirmek için:**

1. Visual Studio 'da, işleme **Ekle** iletişim kutusunu açmak Için **Hata Ayıkla > işleme Ekle** (veya **Ctrl + Alt + P**) öğesini seçin.

   ![Visual Studio 'da Işleme Iliştir iletişim kutusunun ekran görüntüsü (Windows kapsayıcısı) bir bağlantı türünü gösterir.](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. **Bağlantı türünü** **Docker (Windows container)** olarak ayarlayın.
3. **Docker kapsayıcısını Seç** iletişim kutusunu kullanarak **bağlantı hedefini** ayarlamak için **bul...** seçeneğini belirleyin.

    > [!IMPORTANT]
    > Hedef işlem, üzerinde çalıştığı Docker Windows kapsayıcısı ile aynı işlemci mimarisine sahip olmalıdır.

   Hedefin SSH aracılığıyla uzak bir kapsayıcıya ayarlanması şu anda kullanılamıyor ve yalnızca bir Docker Daemon kullanılarak yapılabilir.

    ***Hedefi bir [Docker Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla bir işlem çalıştıran uzak kapsayıcıya ayarlamak için***
    1. **Docker Konağı (Isteğe bağlı)** altında, Daemon ADRESINI (TCP, IP vb.) belirtin ve Yenile bağlantısına tıklayın.

    1. Daemon 'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve Tamam ' ı seçin.

4. **Kullanılabilir işlemler** listesinden karşılık gelen kapsayıcı işlemini seçin ve C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin.

    ![Visual Studio 'da Işleme Iliştir iletişim kutusunun ekran görüntüsü. Bağlantı türü Docker (Windows container) olarak ayarlanır ve dotnet.exe işlem seçilidir.](../debugger/media/docker-attach-complete-windows.png "Windows Docker Iliştirme menüsü tamamlandı")

5. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini seçin ve C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin.