---
title: R ve Docker konteynerleri
description: Nasıl R için Docker konteyner kurmak ve Visual Studio ile onlara bağlanmak için.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c5b4278ab50aac96703f03e74c014d29831f22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62810245"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Visual Studio için R Araçları ile Docker konteynerleri kullanın

R Tools for Visual Studio (RTVS) sürüm 1.3+, [Windows için Docker](https://www.docker.com/docker-windows)yüklemesinin yanı sıra Docker kapsayıcılarıyla çalışmayı destekler.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

1. **Çalışma Alanları** penceresinin **(R Tools** > **Windows** > Çalışma**Alanları)** sağ köşesindeki **Kapsayıcılar** düğmesini seçin. Pencere, Windows için Docker yüklü değilse sizi bilgilendirir ve karşıdan yükleme için bir bağlantı sağlar. Docker'ın yüklenmesi için bilgisayarın yeniden başlatılması gerekebilir.

    ![Konteynerler komutu yla Visual Studio için R Tools (VS2017) çalışma alanları penceresi](media/container-workspaces-window.png)

1. **Kapsayıcılar** penceresinde **Oluştur'u**seçin:

    ![Kapsayıcılar penceresinde komut oluşturma](media/containers-window-create.png)

1. İletişim kutusunda gerekli bilgileri tamamlayın ve **Oluştur'u**seçin. Girdiğiniz kimlik bilgileri, linux'ta daha sonra oturum açtığınızda bir hesap oluşturmak için de kullanılır.

    ![Kapsayıcı oluştururken kapsayıcı adı ve kimlik bilgileri girme](media/containers-window-create-fill.png)

1. RTVS görüntü oluşturmak için biraz zaman alabilir. Visual Studio'daki **Output** penceresi ilerlemeyi gösterir, ancak uzun görüntü indirmeler sırasında pek bir şey yapmıyor gibi görünebilir; sabırlı olmaya hazır olun. Görüntü oluşturulduktan sonra, RTVS kapsayıcıyı başlatır ve **Kapsayıcı** penceresinde görünür. Denetimleri sağ daki duraklayın, kaldırın veya kapsayıcıyı yeniden başlatın.

    ![Tamamlanmış bir kapsayıcıyı gösteren kapsayıcılar penceresi](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

1. **Çalışma Alanları** penceresinin Yerel **Çalışan Kapsayıcılar** bölümü, 5444 numaralı bağlantı noktasında RTVS daemon'u çalıştıran kapsayıcıları görüntüler. (Daemon'un nasıl yapılandırıldığı hakkında ayrıntılı bilgi için [Linux için Remote R Server'a](setting-up-remote-r-service-on-linux.md) bakın.)

    ![Kullanılabilir kapsayıcıları gösteren çalışma alanları penceresi](media/workspaces-window-running-containers.png)

1. Bir kapsayıcıya bağlanmak için, kapsayıcı adını çift tıklatın veya sağdaki ileri ok düğmesini seçin. Bağlandığında, bir **R Interactive** penceresi görürsünüz (bkz. [R Interactive penceresi ile Çalışma):](interactive-repl-for-r-in-visual-studio.md)

    ![Çalışma alanları penceresi ve REPL penceresi bir kapsayıcı için açıldı](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Özel olarak oluşturulmuş görüntüler kullanma

RTVS, aşağıdaki docker dosyasında açıklanan microsoft/rtvs görüntüsü gibi özel olarak oluşturulmuş görüntüler kullanılarak oluşturulan kapsayıcıların yönetimini algılar ve sağlar. Burada kullanılan temel görüntü rtvs-daemon, R 3.4.2 ve ortak R paketleri önceden yüklenmiş. **Not**: Gerektiğinde burada gösterilen kullanıcı adını ve parolayı değiştirin.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Kapsayıcı adını (bağımsız değişkeni) `--name` istediğiniz gibi değiştirerek görüntüyü oluşturmak için aşağıdaki komutu kullanın:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Bağımsız `-p 6056:5444` değişken, RTVS'nin rtvs-daemon'u tespit etmek için kullandığı iç bağlantı noktası 5444 ile 6056 bağlantı noktasını eşler. Kapsayıcı bağlantı noktası 5444'ün ortaya çıkardığı tüm kapsayıcılar **Çalışma Alanları** penceresinde listelenir. Daha sonra, **Workspaces** docker dosyasında farklı kimlik `<<unix>>\ruser1` bilgileri belirtmediğiniz sürece, kullanıcı adı ve parola olarak "foobar" kullanarak bir kapsayıcıya bağlanmak için Çalışma Alanları penceresini kullanabilirsiniz.
