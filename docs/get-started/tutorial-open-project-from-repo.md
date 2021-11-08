---
title: 'Öğretici: Visual Studio bir depoyu bir proje açın'
description: Visual Studio ile bir Git veya Azure DevOps deposundaki bir projeyi açmayı öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 11/05/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fc69410334c4c9bdf8c3538f9aa9f34a1d2f1e1a
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001406"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: bir depodan bir proje açın
F bu öğreticide, bir depoya ilk kez bağlanmak ve ardından bir projeyi açmak için Visual Studio kullanacaksınız.

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker range="vs-2022"

## <a name="open-a-project-from-a-github-repo"></a>GitHub deposundan proje açma

Visual Studio, bir deponun bir projeyi açmayı kolaylaştırır. Visual Studio başlattığınızda bunu yapabilirsiniz veya doğrudan [Visual Studio ıde](visual-studio-ide.md?view=vs-2022&preserve-view=true)içinden yapabilirsiniz.

Aşağıdaki adımları uygulayın:

### <a name="use-the-start-window"></a>Başlangıç penceresini kullanın

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Visual Studio bir depoyu Kopyala iletişim kutusunun ekran görüntüsü.":::

1. Depo konumunu girin veya yazın ve ardından **Kopyala** düğmesini seçin.

    :::image type="content" source="../ide/media/vs-2022/clone-repository-enter-location.png" alt-text="[bir Git deposu URL 'si girdiğiniz Visual Studio depo kopyalama iletişim kutusunun ekran görüntüsü.":::

1. Kullanıcı oturum açma bilgileriniz, **Git Kullanıcı bilgileri** iletişim kutusunda istenebilir. Bilgilerinizi ekleyebilir ya da sağladığı varsayılan bilgileri düzenleyebilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/git-user-information-dialog.png" alt-text="Visual Studio 2022 ' de hesap bilgilerinizi girdiğiniz veya düzenlediğiniz Git kullanıcı bilgileri iletişim kutusunun ekran görüntüsü.":::

    Bilgileri Global. gitconfig 'de ayarla dosyanıza eklemek için **Kaydet** ' i seçin. (Veya daha sonra **iptal**' i seçerek bunu yapmayı seçebilirsiniz.)

    > [!TIP]
    > Visual Studio 'de oturum açma hakkında daha fazla bilgi için [**Visual Studio oturum açma**](../ide/signing-in-to-visual-studio.md?view=vs-2022&preserve-view=true) sayfasına bakın. GitHub hesabınızı kullanarak oturum açmak için nasıl kullanılacağına ilişkin belirli bilgiler için [**Visual Studio sayfasındaki GitHub hesaplarıyla çalışma**](../ide/work-with-github-accounts.md?view=vs-2022&preserve-view=true) bölümüne bakın. Bir güven bildirimi alırsanız ve bunun hakkında daha fazla bilgi edinmek istiyorsanız [Dosyalar ve klasörler için güven ayarlarını yapılandırma](../ide/reference/trust-settings.md?view=vs-2022&preserve-view=true) sayfasına bakın.

### <a name="view-files-in-solution-explorer"></a>Çözüm Gezgini dosyaları görüntüleme

1. sonra, Visual Studio [**Çözüm Gezgini**](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true)içindeki **klasör görünümünü** kullanarak, çözümü depodan yükler.

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Visual Studio 2022 ' de Çözüm Gezgini klasör görünümünün ekran görüntüsü.":::

    Çözüm **görünümünde** bir çözümü,. sln dosyasına çift tıklayarak görüntüleyebilirsiniz.

    Ya da, **görünümleri Değiştir** düğmesini seçip bir çözümün kodunu görüntülemek için **program. cs** ' yi seçebilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-switch-views.png" alt-text="Git 'te Çözüm Gezgini açık olan ve Visual Studio 2022 ' de görünümleri değiştir düğmesi vurgulanmış olan Git 'teki projenin ekran görüntüsü.":::

> [!TIP]
> Varsayılan görünüm, klasör görünümü olarak ayarlanır. **Git** menüsünde çözüm görünümü olarak değiştirebilirsiniz. **Ayarlar**  >  **kaynak denetimi**  >  **git genel Ayarlar**  >  **bir git deposu açarken çözümü otomatik olarak yükle** ' yi seçin.

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>önceden kopyalanmış GitHub deposundan yerel olarak bir proje açın

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **Proje veya çözüm aç**' ı seçin.

    Visual Studio, çözüm veya projenize gözatabileceğiniz bir dosya gezgini örneğini açar ve ardından onu seçerek açabilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/open-local-project-from-cloned-repo.png" alt-text="Visual Studio 2022 ' de ' proje veya çözüm aç ' penceresinin ekran görüntüsü.":::

    > [!TIP]
    > Projeyi veya çözümü kısa süre önce açtıysanız, bunu tekrar **açmak için son** görüntülenen bölümden birini seçin.

    Kodlamaya başlayın!

### <a name="use-the-ide"></a>IDE 'yi kullanma

ayrıca, bir deponun klasör ve dosyalarıyla etkileşim kurmak için Visual Studio ıde 'de **Git** menüsünü veya **Select Repository** denetimini de kullanabilirsiniz.

Aşağıdaki adımları uygulayın:

#### <a name="to-clone-a-repo-and-open-a-project"></a>Depoyu kopyalamak ve bir projeyi açmak için

1. Visual Studio ıde 'de **Git** menüsünü ve ardından **depoyu kopyala**' yı seçin.

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="kopya deposu seçiliyken Visual Studio 2022 ' deki Git menüsünün ekran görüntüsü.":::

1. Aradığınız dosyaları içeren git deposuna bağlanmak için istemleri izleyin.

#### <a name="to-open-local-folders-and-files"></a>Yerel klasörleri ve dosyaları açmak için

1. Visual Studio ıde 'de **Git** menüsünü seçin, **yerel depolar**' ı seçin ve ardından **yerel depoyu aç**' ı seçin.

    :::image type="content" source="../ide/media/vs-2022/git-menu-local-repositories.png" alt-text="yerel depoyla Visual Studio 2022 ' deki Git menüsünün ekran görüntüsü ve açık yerel depoyu gösterir.":::

    Alternatif olarak, **Çözüm Gezgini** aynı görevi gerçekleştirebilirsiniz. Bunu yapmak için **Depo denetimi Seç** ' i seçin, **depoları filtrele** kutusunun yanındaki **üç nokta** simgesini seçin ve ardından **yerel depoyu aç**' ı seçin.

    :::image type="content" source="../ide/media/vs-2022/select-repository-filter-ellipsis.png" alt-text="Dizi Seç denetiminin, üç nokta simgesiyle seçili olduğu ve yerel depoyu aç seçeneğinin ekran görüntüsü.":::

1. Aradığınız dosyaları içeren git deposuna bağlanmak için istemleri izleyin.

## <a name="browse-to-an-azure-devops-server"></a>Bir Azure DevOps Server gidin

Visual Studio kullanarak Azure DevOps Server nasıl gözataöğreneceksiniz.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Azure DevOps için Visual Studio bir depoyu kopyala iletişim kutusunun ekran görüntüsü.":::

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio Azure DevOps vurgulanmış olan ' depoyu kopyala ' iletişim kutusunun ' bir depoya gözatatıon ' bölümünün ekran görüntüsü.":::

1. aradığınız dosyaları barındıran bir Azure DevOps Server bağlanmak için istemleri izleyin.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile GitHub deposundan proje açma

Visual Studio kullanarak bir projeyi GitHub deposundan açtığınızda, sahip olduğunuz sürüme göre değişir. özellikle, sürüm Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümünü yüklediyseniz, Visual Studio kullanabileceğiniz yeni, daha kapsamlı bir tam olarak tümleşik [Git deneyimi](../ide/git-with-visual-studio.md) mevcuttur.

ancak, hangi sürümü yüklediğinizden bağımsız olarak bir projeyi Visual Studio GitHub deposundan her zaman açabilirsiniz.

### <a name="168-and-later"></a>16,8 ve üzeri

işte Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes-history) veya sonraki sürümlerde Git 'i kullanma.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub depoyu kopyalayın ve ardından bir proje açın

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,8 ve üzeri bir depoyu kopyala iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. Depo konumunu girin veya yazın ve ardından **Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki bir Git deposu URL 'si girdiğiniz bir depoyu kopyala iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Kullanıcı oturum açma bilgileriniz, **Git Kullanıcı bilgileri** iletişim kutusunda istenebilir. Bilgilerinizi ekleyebilir ya da sağladığı varsayılan bilgileri düzenleyebilirsiniz.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde hesap bilgilerinizi girdiğiniz veya düzenlediğiniz Git kullanıcı bilgileri iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/git-user-information-dialog.png)

    Bilgileri Global. gitconfig 'de ayarla dosyanıza eklemek için **Kaydet** ' i seçin. (Veya daha sonra **iptal**' i seçerek bunu yapmayı seçebilirsiniz.)

    > [!TIP]
    > Visual Studio 'de oturum açma hakkında daha fazla bilgi için [Visual Studio oturum açma](../ide/signing-in-to-visual-studio.md?view=vs-2019&preserve-view=true) sayfasına bakın. GitHub hesabınızı kullanarak oturum açmak için nasıl kullanılacağına ilişkin belirli bilgiler için, [Visual Studio sayfasındaki GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md?view=vs-2019&preserve-view=true) bölümüne bakın.

    sonra, Visual Studio çözümü otomatik olarak yükler ve depodan açar.

   ![Git 'teki projenin, Visual Studio 2019 sürüm 16,8 ve sonrasında Çözüm Gezgini açık olan ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer.png )

1. Deponuz birden çok çözüm içeriyorsa, bunları Çözüm Gezgini görürsünüz. Çözüm Gezgini ' de **görünümleri Değiştir** düğmesini seçerek çözümlerin listesini görüntüleyebilirsiniz.

   ![Git 'te Çözüm Gezgini açık olan, Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde görünümleri değiştir düğmesi vurgulanmış olan Git 'teki projenin ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Çözüm Gezgini, **klasör görünümünde** kök klasörü açma veya açılacak bir çözüm dosyası seçme seçeneği sunar.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde görünümleri değiştir düğmesini seçtikten sonra Çözüm Gezgini açık olan Git 'teki. sln dosyasının ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Görünümü değiştirmek için **görünümleri Değiştir** düğmesini yeniden seçin.

    > [!TIP]
    > ayrıca, bir depoyu kopyalamak ve bir projeyi açmak için Visual Studio ıde 'deki **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü.](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>önceden kopyalanmış GitHub deposundan yerel olarak bir proje açın

1. Visual Studio 2019 sürüm 16,8 veya üstünü açın.

1. Başlangıç penceresinde, **Proje veya çözüm aç**' ı seçin.

    Visual Studio, çözüm veya projenize gözatabileceğiniz bir dosya gezgini örneğini açar ve ardından onu seçerek açabilirsiniz.

   ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde ' proje veya çözüm aç ' penceresinin ekran görüntüsü.](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Projeyi veya çözümü kısa süre önce açtıysanız, bunu tekrar **açmak için son** görüntülenen bölümden birini seçin.

    > [!TIP]
    > ayrıca, daha önce klonladığınız bir depodan yerel klasörleri ve dosyaları açmak için Visual Studio ıde 'deki **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü, yerel depolar seçeneği genişletilir.](../ide/media/vs-2019/git-menu-local-repositories.png)

    Kodlamaya başlayın!

### <a name="167-and-earlier"></a>16,7 ve öncesi

Visual Studio 2019 sürüm [**16.7**](/visualstudio/releases/2019/release-notes-history) veya önceki bir sürümde Git'i nasıl kullanabileceğiniz burada açık ve açık bir şekilde açıklandı.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Bir GitHub kopyalama ve sonra bir proje açma

1. 2019 Visual Studio 16.7 veya önceki bir sürümü açın.

1. Başlangıç penceresinde Kopyala'ya tıklayın **veya kodu kontrol edin.**

   ![2019 sürüm 16.7 ve Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![2019 sürüm 16.7 ve Visual Studio 'Kodu kopyala veya iade edin' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio, projeyi repodan açar.

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![2019 Çözüm Gezgini 16.7 ve Visual Studio açılan listesinin ekran görüntüsü.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa açılır menüde "Çözüm Bulunamadı" yazıyor. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

    Kodlamaya başlama!

## <a name="connect-to-an-azure-devops-server-with-visual-studio-2019"></a>Bağlan 2019 Azure DevOps Server bir Visual Studio'a

Visual Studio 2019 kullanarak bir Azure DevOps Server bağlanarak ne göreceğiniz, sahip olduğunuz sürüme bağlıdır. Özellikle, [**sürüm 16.8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümü yüklemişsanız, kullanıcı arabirimini Visual Studio'de yeni ve daha tam olarak tümleştirilmiş bir Git deneyimine uyum [sağlayacak şekilde](../ide/git-with-visual-studio.md) Visual Studio.

Ancak, hangi sürümü yüklemiş olur olun, her zaman Azure DevOps Server bir Visual Studio.

### <a name="168-and-later"></a>16.8 ve sonrası

1. 2019 Visual Studio [**16.8 veya sonraki bir sürümü**](/visualstudio/releases/2019/release-notes-history) açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde depo kopyalama iletişim kutusunun ekran Azure DevOps.](../ide/media/vs-2019/clone-repository.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

    ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Project'a Bağlan' iletişim kutusunun 'Depoya gözat' bölümünün ekran görüntüsü.](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 Bağlan 16.8 ve sonraki sürümlerden oluşturulan 'Project'a ekle' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Bağlanmak için önceden doldurulmuş bir repos listesi görmüyorsanız,  sunucu URL'si girmek için Azure DevOps Server Ekle'yi seçin. (Alternatif olarak, mevcut bir hesap eklemek veya bir Azure DevOps Server hesabı oluşturmak için bağlantılar içeren bir "Sunucu bulunamadı" Azure DevOps olabilir.)

   Ardından Visual Studio ve **Çözüm Gezgini** gösteren bir dosya açılır.

1. Takım Gezgini **eylemlerini** görüntülemek için Azure DevOps seçin.

      ![2019 Takım Gezgini 16.8 ve sonraki sürümlerden oluşturulan 'Visual Studio Takım Gezgini' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>16.7 ve önceki sürümler

1. 2019 Visual Studio [**16.7 veya önceki bir sürümü**](/visualstudio/releases/2019/release-notes-history) açın.

1. Başlangıç penceresinde Kopyala'ya tıklayın **veya kodu kontrol edin.**

   ![2019 sürüm 16.7 ve Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde yer alan 'Depoya göz atma Azure DevOps' bölümünün yer Visual Studio ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerden oluşturulan 'Bağlan bir Project' iletişim kutusunun ekran görüntüsü.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

   Visual Studio, **Takım Gezgini** tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki sürümlerindeki uygulama penceresinin ekran görüntüsü.](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için Klasör Görünümünü **Göster bağlantısını** seçin.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki bir sürümde yer alan Çözümler bölümünün ekran görüntüsü.](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **,** Çözüm Gezgini.

1. Açılacak **bir çözüm dosyası** (özel olarak bir .sln dosyası) aramak için Çözümler ve Klasörler bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde Takım Gezgini 'Çözümler ve Klasörler' bildiriminin ekran görüntüsü.](./media/open-proj-repo-solutions-folders.png)

   Bir çözüm dosyanız yoksa, 'Çözüm Bulunamadı' iletisi görüntülenir. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2017"></a>Visual Studio 2017 ile GitHub bir proje açma

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Kaynak Denetiminden **Dosya** >  > **Aç Aç'ı seçin.**

   Takım Gezgini **- Bağlan** bölmesi açılır.

    ![Takım Gezgini IDE içindeki Visual Studio penceresi](./media/open-proj-repo-team-explorer.png)

1. Yerel **Git Depoları bölümünde Kopyala'ya** **tıklayın.**

    ![Yerel Git Depoları bölümünden Kopyala'ya tıklayın](./media/open-proj-repo-local-git-repo-clone.png)

1. * yazarak kopyalanan **Git** depolarının URL'sini girin _ kutusuna depo için URL yazın veya yapıştırın ve _*Enter** tuşuna basın. (Oturum açma istemiyle oturum GitHub, oturum açın.)

   Bu Visual Studio sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. Çözümler listesini görüntülemek için *yukarıdaki Çözümler ve Klasörler'e tıklayın iletisi görüntülenir.* Çözümler **ve Klasörler'i seçin.**

   ![Dosyadan "Çözümler ve Klasörler" Çözüm Gezgini](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![Açılır listeden neleri açmak Çözüm Gezgini seçin.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa, açılır menüde "Çözüm Bulunamadı" olur. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirme

Önceki bölümde tamamlamış olduğunu işi kontrol etmek için aşağıdaki animasyonu görüntüebilirsiniz.

   ![Visual Studio 2017'GitHub bir Visual Studio açma animasyonu.](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-with-visual-studio-2017"></a>2017'de Azure DevOps bir Visual Studio açma

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Kaynak Denetiminden **Dosya** >  > **Aç Aç'ı seçin.**

   Takım Gezgini **- Bağlan** bölmesi açılır.

    ![Takım Gezgini IDE içindeki Visual Studio penceresi.](./media/open-proj-repo-team-explorer.png)

1. Veri Azure DevOps bağlanmanın iki yolu vardır:

      - Barındırılan **Hizmet Sağlayıcıları bölümünde Bağlan...** öğesini **seçin.**

        ![Takım Gezgini IDE'nin Takım Gezgini Barındırıla Visual Studio n Hizmet Sağlayıcıları bölümü.](./media/open-proj-repo-azure-devops.png)

      - Bağlantıları **Yönet açılan** listesinde Bir **Bağlan... seçeneğini Project.**

        ![Visual Studio IDE içindeki Takım Gezgini penceresinin Bağlantıları Visual Studio.](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Dosyadan Bağlan 'Project' iletişim kutusu Visual Studio.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

1. Bu Visual Studio sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. Çözümler listesini görüntülemek için *yukarıdaki Çözümler ve Klasörler'e tıklayın iletisi görüntülenir.* Çözümler **ve Klasörler'i seçin.**

      ![Takım Gezgini'daki "Çözümler ve Klasörler" Visual Studio.](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve Klasörler" açılır menüsünde bir çözüm dosyası (özel olarak bir .sln dosyası) görüntülenir. Seçin ve Visual Studio açılır.

   Bir çözüm dosyanız yoksa, açılır menüde "Çözüm Bulunamadı" ifadesini görünür. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki dile özgü öğreticilerden herhangi birini öğrenmekten bağımsız olarak:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript,** **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](../ide/git-with-visual-studio.md)
- [Git ile Takım Gezgini yan yana karşılaştırma](../ide/git-team-explorer-feature-comparison.md)
- [Microsoft Learn: Kullanmaya başlayın Git ve GitHub ile Visual Studio](/learn/modules/visual-studio-github-push/)
- [Microsoft Learn: Kullanmaya başlayın ile Azure DevOps](/learn/modules/get-started-with-devops/)
- [Azure DevOps Services: Kullanmaya başlayın ve Azure Repos ile Visual Studio](/azure/devops/repos/git/gitquickstart/)