---
title: Visual Basic ile ilk konsol uygulamanızı oluşturma
description: Visual Basic ile Visual Studio bir basit Merhaba Dünya konsol uygulamasının nasıl oluşturulduğunu öğrenin ve adım adım.
ms.custom: vs-acquisition
ms.date: 09/14/2021
ms.topic: quickstart
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 0ece22de8280742a099432fd5b3e527631718cfb
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427878"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>hızlı başlangıç: Visual Basic ile Visual Studio ilk konsol uygulamanızı oluşturma

bu 5-10 dakika içinde Visual Studio tümleşik geliştirme ortamına (ıde) giriş yaparken, konsolunda çalışan basit bir Visual Basic uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

ilk olarak, bir Visual Basic uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual Basic**' i genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından projeyi *HelloWorld* olarak adlandırın.

   ![konsol uygulaması (.net Core) proje şablonu Visual Studio ıde 'deki yeni Project iletişim kutusu](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

   **konsol uygulaması (.net Core)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısına tıklayın.

   ![yeni Project iletişim kutusundan Visual Studio Yükleyicisi aç bağlantısına tıklayın](../ide/media/vb-open-visual-studio-installer-hello-world.png)

   Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükü](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Bu hızlı başlangıçtaki ekran görüntüleri koyu temasını kullanır. koyu tema kullanmıyorsanız, ancak bunu yapmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio ıde ve düzenleyiciyi kişiselleştirme](quickstart-personalize-the-ide.md) sayfasına bakın.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' yeni proje oluştur ' seçeneği vurgulanmış şekilde Visual Studio başlangıç penceresini gösteren ekran görüntüsü.](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde, dil listesinden **Visual Basic** ' yi seçin. ardından, proje türleri listesinden Platform listesinden ve **konsolundan** **Windows** ' yi seçin.

   Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="dil, platform ve proje türü filtrelerinde seçili ' Visual Basic ', ' Windows ' ve ' Console ' ile ' yeni proje oluştur ' penceresini gösteren ekran görüntüsü. ' Konsol uygulaması ' proje şablonu vurgulanır.":::

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Daha fazla araç ve özellik yükler ' bağlantısını gösteren ve ' aradığınızı bulma ' iletisinde vurgulanan ekran görüntüsü.](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > sonra, Visual Studio Yükleyicisi **.net Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi ' .net Core platformlar arası geliştirme ' iş yükünü gösteren ekran görüntüsü.](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **İleri**' yi seçin.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-console-project-hello-world.png" alt-text="' yeni projenizi yapılandır ' penceresinde, Project adı alanına girilen ' HelloWorld ' ile gösterilen ekran görüntüsünde.":::

1. **Ek bilgi** penceresinde **.NET Core 3,1** , hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.NET Core 3,1**' i seçin. Ardından **Oluştur**' u seçin.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="Framework alanında ' .NET Core 3,1 ' ile birlikte ek bilgi penceresini gösteren ekran görüntüsü.":::

   Visual Studio yeni projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="' yeni proje oluştur ' seçeneği vurgulanmış şekilde Visual Studio başlangıç penceresini gösteren ekran görüntüsü.":::

1. **yeni proje oluştur** penceresinde, dil listesinden **Visual Basic** ' yi seçin. ardından, proje türleri listesinden Platform listesinden ve **konsolundan** **Windows** ' yi seçin.

   Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2022/vb-create-new-project-console-net-core.png" alt-text="dil, platform ve proje türü filtrelerinde seçili ' Visual Basic ', ' Windows ' ve ' Console ' ile ' yeni proje oluştur ' penceresini gösteren ekran görüntüsü. ' Konsol uygulaması ' proje şablonu vurgulanır.":::

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="' Daha fazla araç ve özellik yükler ' bağlantısını gösteren ve ' aradığınızı bulma ' iletisinde vurgulanan ekran görüntüsü.":::
   > 
   > sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.
   >
   > :::image type="content" source="media/vs-2022/dot-net-core-xplat-dev-workload.png" alt-text="Visual Studio Yükleyicisi ' .net masaüstü geliştirme ' iş yükünü gösteren ekran görüntüsü.":::
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2022/vb-name-your-project-hello-world.png" alt-text="Project adı alanında ' HelloWorld ' ile ' yeni projeyi yapılandır ' penceresini gösteren ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.net 6,0** hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **Framework** açılan listesinde **.net 6,0** ' i seçin. Ardından **Oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/vb-target-framework.png" alt-text="Framework alanında ' .NET 6,0 ' ile birlikte ek bilgi penceresini gösteren ekran görüntüsü.":::

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

::: moniker range="vs-2019"

Visual Basic proje şablonunuzu seçip projenizi adlandırın Visual Studio, sizin için basit bir "Merhaba Dünya" uygulaması oluşturur. <xref:System.Console.WriteLine%2A>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağırır Konsol penceresinde.

![Visual Basic proje şablonundaki varsayılan ' Merhaba Dünya ' kodu gösteren ekran görüntüsü.](../ide/media/vb-console-helloworld-template.png)

IDE 'de **HelloWorld** düğmesini seçerseniz, programı hata ayıklama modunda çalıştırabilirsiniz.

![Visual Studio araç çubuğunda vurgulanan ' Merhaba Dünya ' düğmesini gösteren ekran görüntüsü.](../ide/media/vb-console-hello-world-button.png)

uygulama Microsoft Visual Studio hata ayıklama konsolunda çalıştığında, bir tuşa basana kadar konsol penceresi açık kalır. 

Bununla birlikte, dosya Gezgini 'nde *HelloWorld.exe* gidin ve çalıştırırsanız, `Main` yordam tek bir deyimin çalıştırıldıktan sonra ve konsol penceresi hızlı bir şekilde kapandıktan sonra sonlanır.

### <a name="add-some-code&quot;></a>Kod ekleme

Uygulamayı duraklatmak için bazı kodlar ekleyelim ve sonra Kullanıcı girişi soralım.

1. Yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine%2A> :

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

   Bu, bir tuşa basarak programı duraklatır.

1. Menü **çubuğunda Build** > **Build Solution** öğesini seçin.

   Bu, programınızı bir tam zamanında (JıT) derleyicisi tarafından ikili koda dönüştürülen bir ara dile (IL) derler.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Çözüm Gezgini** menüsünde, projeniz için bağlam menüsünü açmak üzere **HelloWorld** öğesine sağ tıklayın. Sonra, **Dosya Gezgini 'Nde klasörü aç**' ı seçin.

1. **Bin > hata ayıklama > net 6.0** klasöründe *HelloWorld.exe* dosyasına gidin ve çalıştırın.

Artık uygulamanız konsolunda çalışır ve konsol penceresini kapatmak için herhangi bir tuşa bastığımda açık kalır.

   ![Çalışan Merhaba Dünya konsol uygulamasını gösteren ekran görüntüsü. Uygulamada ' Merhaba Dünya! ' iletileri görüntülenir ve ' devam etmek için herhangi bir tuşa basın '.](../ide/media/vb-console-hello-world-press-any-key.png)

::: moniker-end

::: moniker range=">=vs-2022&quot;

Visual Basic proje şablonunuzu seçip projenizi adlandırın Visual Studio basit bir &quot;Merhaba Dünya!&quot; oluşturur sizin için uygulama. **Program. vb** dosyası <xref:System.Console.WriteLine%2A> &quot;Merhaba Dünya!&quot; değişmez dizesini göstermek için yöntemini çağıran varsayılan kodu içerir Konsol penceresinde.

:::image type=&quot;content&quot; source=&quot;media/vs-2022/vb-console-hello-world-template.png&quot; alt-text=&quot;Program. vb dosyasında varsayılan ' Merhaba Dünya ' kodunu gösteren ekran görüntüsü.&quot;:::

Varsayılan &quot;   + HelloWorld&quot; kodunu hata ayıklama modunda çalıştırmak için HelloWorld düğmesini seçin veya CTRL **F5** tuşuna basın.

:::image type=&quot;content&quot; source=&quot;media/vs-2022/vb-console-hello-world-button.png&quot; alt-text=&quot;Visual Studio araç çubuğunda vurgulanan ' HelloWorld ' düğmesini gösteren ekran görüntüsü.&quot;:::

Uygulama hata ayıklama konsolunda Microsoft Visual Studio, siz bir tuşa basana kadar konsol penceresi açık kalır. 

Ancak,HelloWorld.exe'Dosya Gezgini  çalıştırmanız, tek deyimi yürütülür ve konsol penceresi hızla `Main` kapanır.

### <a name=&quot;add-some-code&quot;></a>Kod ekleme

Uygulamayı duraklatmak ve ardından kullanıcı girişi istemek için biraz kod ek o zaman.

1. yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu <xref:System.Console.WriteLine%2A> ekleyin:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

   Bu kod, siz bir tuşa basana kadar programı duraklatıyor.

1. Menü çubuğunda Derleme  > **Çözümü'yü seçin.**

   Çözümü derle, programınızı tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülen bir ara dil (IL) olarak derler.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Bu **Çözüm Gezgini** projenizin bağlam menüsünü açmak için **HelloWorld'e** sağ tıklayın. Ardından, içinde **Klasör Aç'ı Dosya Gezgini.**

1.  **net6.0HelloWorld.exedebug > klasöründeki >** dosyasına gidin ve çalıştırın.

Artık uygulamanız konsolda çalışır ve konsol penceresini kapatmak için herhangi bir tuşa basana kadar açık kalır.

   :::image type="content" source="media/vs-2022/vb-console-hello-world-press-any-key.png" alt-text="Çalışan HelloWorld konsol uygulamasını gösteren ekran görüntüsü. Uygulama 'Merhaba Dünya!' ve 'Devam etmek için herhangi bir tuşa basın' iletilerini görüntüler.":::

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! Visual Basic ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin.

> [!div class="nextstepaction"]
> [Kullanmaya başlayın Visual Basic ile Visual Studio](../get-started/visual-basic/tutorial-console.md)
