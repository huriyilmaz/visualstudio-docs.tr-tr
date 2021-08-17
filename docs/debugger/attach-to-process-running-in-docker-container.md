---
title: Docker kapsayıcısı üzerinde çalışan bir işleme ekleme
description: Visual Studio kullanarak Docker kapsayıcısı çalıştıran bir uygulamada hata ayıklamayı Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: bf895fefa858c8445d7a625c946821afa9ce3ab8b609d66059ad52149c97dda3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346186"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Docker kapsayıcısı üzerinde çalışan bir işleme ekleme 

Windows Docker Kapsayıcısı'Windows Linux .NET Core Docker kapsayıcısı içinde çalışan uygulamaların hatasını ayıklamak için Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Linux Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

İşleme Ekle iletişim kutusunu Visual Studio yerel veya uzak makinenizin Linux .NET Core Docker kapsayıcısı içinde çalışan bir işleme hata **ayıklayıcısını** iliştirebilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için .NET Core Platformlar Arası Geliştirme iş yükünü yüklemeniz ve kaynak koda yerel erişiminizin olması gerekir.

**Linux Docker kapsayıcısı içinde çalışan bir işleme eklemek için:**

1. Bu Visual Studio İşleme Ekle **(CTRL+ALT+P)** > Hata Ayıkla'ya seçerek İşleme Ekle **iletişim** kutusunu açın.

![Docker (Linux Kapsayıcısı) bağlantı türünü Visual Studio İşlem ekle iletişim kutusunun ekran görüntüsü.](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Bağlantı türü **olarak** **Docker (Linux Kapsayıcısı) olarak ayarlayın.**
3. Bul... **öğesini** seçerek Docker **Kapsayıcısı** Seç **iletişim kutusu aracılığıyla Bağlantı hedefini** ayarlayın.

    Docker kapsayıcısı işleminin hatasını yerel olarak veya uzaktan ayıkabilirsiniz.

    **Docker kapsayıcısı işleminin hatasını yerel olarak ayıklamak için:**
    1. **Docker CLI ana bilgisayar'ı** Yerel **Makine olarak ayarlayın.**
    1. Listeden eklemek istediğiniz çalışan kapsayıcıyı seçin ve Tamam'a **tıklayın.**

    ![Docker Kapsayıcı Menüsü'ne tıklayın](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Docker kapsayıcı işleminin hatasını uzaktan ayıklamak için:**

    > [!NOTE]
    > Docker kapsayıcısı içinde çalışan bir işleme uzaktan bağlanmak için iki seçenek vardır. SSH kullanmak için ilk seçenek, yerel makinenize Docker araçları yüklü değilseniz idealdir.  Yerel olarak docker araçları yüklüyse ve uzak istekleri kabul etmek üzere yapılandırılmış bir Docker daemon'uz varsa, Docker daemon'larını kullanarak ikinci seçeneği deneyin.

    1. ***SSH aracılığıyla uzak bir makineye bağlanmak için:***
        1. Uzak bir sisteme bağlanmak için **Ekle...** öğesini seçin.<br/>
        ![Bağlan Sisteme Yükleme](../debugger/media/connect-remote-system.png "Bağlan Sisteme Yükleme")
        1. SSH veya daemon'a başarıyla bağlanın ve Tamam'a bağlanın. 

    1. ***Hedefi [Docker daemon'ı](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla işlem çalıştıran uzak kapsayıcıya ayarlamak için***
        1. Docker ana bilgisayarı (İsteğe **bağlı)** altında daemon adresini (TCP, IP vb.) belirtin ve yenileme bağlantısına tıklayın.
        1. Daemon'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve Tamam'a **tıklayın.**

4. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini  **seçin ve** Ekle'yi seçerek C# kapsayıcı işleminizin hata ayıklamasını Visual Studio!

    ![Visual Studio'da İşleme Ekle iletişim kutusunun ekran görüntüsü. Bağlantı türü Docker (Linux Kapsayıcısı) olarak ayarlanır ve dotnet işlemi seçilir.](../debugger/media/docker-attach-complete.png "Tamamlandı Linux Docker Ekleme Menüsü")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Windows Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

İşleme İldir iletişim kutusunu Visual Studio yerel makinenizin Windows Docker kapsayıcısı içinde çalışan bir işleme hata **ayıklayıcı** iliştirebilirsiniz.

> [!IMPORTANT]
> Bu özelliği bir .NET Core işlemiyle kullanmak için .NET Core Platformlar Arası Geliştirme iş yükünü yüklemeniz ve kaynak koda yerel erişiminizin olması gerekir.

**Windows Docker kapsayıcısı içinde çalışan bir işleme eklemek için:**

1. bu Visual Studio, İşleme **>** Ekle (veya **CTRL+ALT+P**) seçeneğini kullanarak İşleme Ekle iletişim **kutusunu** açın.

   ![Docker Bağlantı türünü (Visual Studio Kapsayıcı) gösteren İşleme Ekle iletişim Windows kutusunun ekran görüntüsü.](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Bağlantı **türü'lerini** **Docker (Windows Container) olarak ayarlayın.**
3. Docker Kapsayıcısı Seç iletişim **kutusunu kullanarak Bağlantı** **hedefini ayarlamak için** **Bul...** öğesini seçin.

    > [!IMPORTANT]
    > Hedef işlem, üzerinde çalıştır konusu olan Docker Windows işlemci mimarisine sahip olması gerekir.

   Hedefi SSH aracılığıyla uzak kapsayıcıya ayarlama şu anda kullanılamıyor ve yalnızca Docker daemon'ı kullanılarak yapılabilir.

    ***Hedefi [Docker daemon'ı](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla işlem çalıştıran uzak kapsayıcıya ayarlamak için***
    1. Docker ana bilgisayarı (İsteğe **bağlı)** altında daemon adresini (TCP, IP vb.) belirtin ve yenileme bağlantısına tıklayın.

    1. Daemon'a başarıyla bağlandıktan sonra iliştirmek için çalışan bir kapsayıcı seçin ve Tamam'ı seçin.

4. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini **seçin ve C#** kapsayıcı **işleminizin** hata ayıklamasını başlatmak için Ekle'yi seçin.

    ![Visual Studio'daki İşleme Ekle iletişim kutusunun ekran görüntüsü. Bağlantı türü Docker (Windows Container) olarak ayarlanır ve dotnet.exe işlemi seçilir.](../debugger/media/docker-attach-complete-windows.png "Docker Windows Menüsü Tamamlandı")

5. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini  seçin ve C# kapsayıcı işleminizin hata ayıklamasını başlatmak için Ekle'yi seçin.