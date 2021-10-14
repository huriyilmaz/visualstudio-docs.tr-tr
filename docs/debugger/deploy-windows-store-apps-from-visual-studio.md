---
title: UWP uygulamalarını | Microsoft Docs
description: Universal Windows Platform (UWP) uygulamalarını Visual Studio. Dağıtım için bir yerel veya uzak hedef cihaz belirtin. Dağıtım seçeneklerini anlama.
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: e8b785a71bc096a1bcb74f1be2a14cc2ba2c9f5d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969833"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Visual Studio’dan UWP uygulamaları dağıtma

Dağıtım Visual Studio işlevi, hedef cihaz üzerinde uygulama ile oluşturulan UWP uygulamalarını Visual Studio ve kaydedmektedir. Uygulamanın tam olarak nasıl kaydedildiklerine, hedef cihazın yerel mi yoksa uzak mı olduğu bağlıdır:

- Hedef yerel makine olduğunda Visual Studio, Visual Studio derleme klasöründen kaydetmesini sağlar.

- Hedef uzak bir cihaz olduğunda, Visual Studio dosyaları uzak makineye kopyalar ve uygulamayı o cihaza kopyalar.

Hata Ayıklamayı Başlat seçeneğini (Klavye: F5)  veya Hata Ayıklama Olmadan Başlat seçeneğini  (Klavye: CTRL + F5) kullanarak uygulamanıza hata ayıklama işlemi Visual Studio dağıtım otomatiktir. Uygulamanızı el ile de dağıtabilirsiniz. El ile dağıtım aşağıdaki senaryolarda yararlıdır:

- Yerel veya uzak makinede geçici test.

- Hata ayıklamak istediğiniz başka bir uygulamayı başlatacak bir uygulama dağıtma.

- Başka bir uygulama veya yöntem tarafından başlatıldıkları zaman hata ayıklanacak bir uygulamayı dağıtma.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> UWP uygulaması dağıtma
 Uygulamayı el ile dağıtmak basit bir işlemdir:

1. Uzak bir cihaza dağıtıyorsanız, uygulamanın başlangıç projesinin özellik projesi sayfasında cihazın adını veya IP adresini belirtin. (Bunu yapma adımları bu konuda daha ayrıntılı olarak listelenmiştir.)

2. Hata ayıklayıcı Visual Studio çubuğunda, Hata Ayıklamayı Başlat düğmesinin yanındaki açılan **listeden dağıtım hedefini** seçin.

     ![Yerel Makinede Çalıştır](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. Derleme menüsünde **Dağıt'ı** **seçin**

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Uzak cihaz belirtme

**Önkoşullar**

Uzak Windows 10 geliştirici modunu [etkinleştirmeniz gerekir.](/windows/uwp/get-started/enable-your-device-for-development) Creator'Windows 10 veya sonraki bir sürümü çalıştıran cihazlarda, uygulamanızı dağıtarak uzak araçlar otomatik olarak yüklenir. Daha fazla bilgi için [bkz. Yüklü uygulama paketinde hata ayıklama.](../debugger/debug-installed-app-package.md)

> [!NOTE]
> Ön Oluşturucu'nun Windows 10 sürümlerinde, Visual Studio için Uzak Araçlar uzak cihaza yük olmalı ve uzaktan hata ayıklayıcı çalışıyor olmalı.

Dağıtım, uygulama dosyalarını uzak cihaza göndermek için uzaktan hata ayıklayıcı ağ kanalını kullanır.

#### <a name="to-specify-a-remote-device"></a>Uzak cihaz belirtmek için

1. Başlangıç projesinin Hata Ayıklama özelliği sayfasında, bir uzak dağıtım hedefinin adını veya IP adresini belirtin.

2. Hata ayıklama özelliği sayfasını açmak için, Çözüm Gezgini menüsünden **Özellikler'i** seçin.

3. Ardından özellik **sayfaları penceresinde** Hata ayıkla düğümünü seçin.

4. Hedef **cihaz için** Uzak **Makine'yi seçin.**

5. Uzak **makine altında** Bul'a **tıklayın.**

6. Uzak cihazın adını veya IP adresini yazabilirsiniz veya Uzak Bağlantı iletişim **kutusundan cihazı** seçebilirsiniz.

    ![Uzaktan Hata Ayıklayıcı Bağlantısını Seç iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Uzaktan **Bağlantı iletişim** kutusu, yerel ağ alt ağına ve ethernet kablosuyla doğrudan Visual Studio cihazları görüntüler.

   **C++ proje sayfasında uzak cihazı belirtme**

   ![C&#43;&#43; hata ayıklama için proje özelliklerini içerir](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Başlatmak **için Hata Ayıklayıcı** listesinden **Uzaktan Hata Ayıklayıcı'ya** tıklayın.

8. Makine Adı kutusuna uzak cihazın ağ **adını** girin. Veya Uzaktan Hata Ayıklayıcı Bağlantısını Seç iletişim kutusundan cihazı seçmek için kutuda aşağı oku seçebilirsiniz.

   **Visual C# ve Visual Basic proje sayfasında uzak cihazı belirtme**

   ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Hedef **Cihaz listesinden** Uzak **Makine'yi** seçin.

10. Uzak Makine kutusuna uzak cihazın ağ adını girin  veya **Uzak** Hata Ayıklayıcı Bağlantısını Seç iletişim kutusundan cihazı seçmek için **Bul'a** tıklayın.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Dağıtım seçenekleri

Başlangıç projesinin Hata Ayıklama özelliği sayfasında aşağıdaki dağıtım seçeneklerini ayarlayın.

**Ağ Geri Döngüye İzin Ver**

Güvenlik nedeniyle, standart bir şekilde yüklenmiş bir UWP veya uygulamanın yüklü olduğu cihaza ağ [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] çağrıları yapmalarına izin verilmez. Varsayılan olarak, Visual Studio dağıtım dağıtılan uygulama için bu kuraldan bir muafiyet oluşturur. Bu muafiyet, iletişim yordamlarını tek bir makinede test etmek için izin verir. Uygulamanızı uygulamasına göndermeden [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] önce, muafiyet olmadan test edin.

Ağ geri döngü muafiyeti uygulamasını kaldırmak için:

- C# ve Hata ayıklama Visual Basic sayfasında Ağ Geri Döngüye İzin **Ver onay kutusunun işaretini** kaldırın.

- C++ Hata Ayıklama özelliği sayfasında, Ağ Geri Döngüye **İzin Ver değerini** Hayır olarak **ayarlayın.**

**Başlatmayın, ancak başlatıldığında kodumda hata ayıklama (C# ve Visual Basic) / Uygulamayı Başlatma (C++)**

Dağıtımı, uygulama başlatıldığında otomatik olarak bir hata ayıklama oturumu başlatacaktır şekilde yapılandırmak için:

- C# ve hata Visual Basic sayfasında Başlatma'ya tıklayın, ancak başlatıldığında kodumda hata ayıkla **onay** kutusunu işaretleyin.

- C++ Hata Ayıklama özelliği sayfasında Uygulamayı Başlat **değerini Evet** olarak **ayarlayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş uzaktan dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md)
- [Visual Studio’dan uygulamaları çalıştırma](debugging-windows-store-and-windows-universal-apps.md)
