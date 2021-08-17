---
title: R ve Docker Kapsayıcıları
description: R için Docker kapsayıcılarını ayarlama ve Visual Studio ile bunlara bağlanma.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 4b19e604b052e6f573ff6d07e0830cf4d0af8c37
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060472"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Visual Studio için R Araçları ile docker kapsayıcıları kullanma

[Docker for Windows](https://www.docker.com/docker-windows)yüklemesiyle birlikte Visual Studio için R Araçları (rtvs) sürüm 1.3 +, docker kapsayıcılarıyla çalışmayı destekler.

## <a name="create-a-container"></a>Kapsayıcı oluşturma

1. **çalışma alanları** penceresinin sağ köşesindeki **kapsayıcılar** düğmesini seçin (**R araçları**  >  **Windows**  >  **çalışma alanları**). bu pencere, Docker for Windows yüklü değilse ve indirme için bir bağlantı sağlıyorsa size bildirir. Docker 'ı yüklemek için bilgisayarın yeniden başlatılması gerekebilir.

    ![kapsayıcılar komutuyla Visual Studio için R Araçları (VS2017) içindeki çalışma alanları penceresi](media/container-workspaces-window.png)

1. **Kapsayıcılar** penceresinde **Oluştur**' u seçin.

    ![Kapsayıcılar penceresinde Oluştur komutu](media/containers-window-create.png)

1. İletişim kutusunda gerekli bilgileri doldurun ve **Oluştur**' u seçin. Girdiğiniz kimlik bilgileri, daha sonra oturum açmanız gereken Linux üzerinde bir hesap oluşturmak için de kullanılır.

    ![Kapsayıcı oluştururken kapsayıcı adı ve kimlik bilgilerini girme](media/containers-window-create-fill.png)

1. RTVS 'nin görüntüyü oluşturması biraz zaman alabilir. Visual Studio 'daki **çıkış** penceresinde ilerleme durumu gösterilir, ancak uzun görüntü indirmeleri sırasında çok fazla gerçekleşmeyebilir; hasta olacak şekilde hazırlıklı olun. Görüntü oluşturulduktan sonra RTVS kapsayıcıyı başlatır ve **kapsayıcı** penceresinde görünür. Sağ taraftaki denetim kapsayıcıyı durdurur, kaldırır veya yeniden başlatır.

    ![Tamamlanmış kapsayıcıyı gösteren kapsayıcılar penceresi](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>bir kapsayıcıya Bağlan

1. **Çalışma alanları** penceresinin **yerel olarak çalışan kapsayıcılar** bölümünde, bağlantı noktası 5444 ' de rtvs Daemon çalıştıran kapsayıcılar görüntülenir. (Arka plan programının nasıl yapılandırıldığına ilişkin ayrıntılar için bkz. [uzak Linux için R Server](setting-up-remote-r-service-on-linux.md) .)

    ![Kullanılabilir kapsayıcıları gösteren çalışma alanları penceresi](media/workspaces-window-running-containers.png)

1. Bir kapsayıcıya bağlanmak için kapsayıcı adına çift tıklayın veya sağ ok düğmesini sağ tarafında seçin. Bağlandığınızda, bir **R etkileşim** penceresi görürsünüz (bkz [. R etkileşim penceresiyle çalışma](interactive-repl-for-r-in-visual-studio.md)):

    ![Bir kapsayıcı için çalışma alanları penceresi ve REPL penceresi açıldı](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Özel olarak oluşturulmuş görüntüleri kullanma

RTVS, aşağıdaki Docker dosyasında açıklanan Microsoft/rtvs görüntüsü gibi özel olarak oluşturulmuş görüntüler kullanılarak oluşturulan kapsayıcıların yönetimini algılar ve yönetimine izin verir. Burada kullanılan temel görüntüde rtvs-Daemon, R 3.4.2 ve ortak R paketleri önceden yüklenmiş olarak bulunur. **Note**: gerektiğinde burada gösterilen kullanıcı adını ve parolayı değiştirin.

```docker
FROM mcr.microsoft.com/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Görüntüyü derlemek için aşağıdaki komutu kullanın, kapsayıcı adını ( `--name` bağımsız değişkeni) istediğiniz şekilde değiştirerek:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444`Bağımsız değişken, rtvs 'in rtvs-Daemon ' ı algılaması için 6056 numaralı bağlantı noktasını iç bağlantı noktası 5444 ' e eşler. 5444 kapsayıcı bağlantı noktasını sunan herhangi bir kapsayıcı, **çalışma alanları** penceresinde listelenir. Daha sonra,  `<<unix>>\ruser1` Docker dosyasında farklı kimlik bilgileri belirtmediğiniz sürece Kullanıcı adı ve parola olarak "foobar" kullanarak bir kapsayıcıya bağlanmak için çalışma alanları penceresini kullanabilirsiniz.
