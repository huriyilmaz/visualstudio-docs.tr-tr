---
title: 'Öğretici: Visual Studio bir depoyu bir proje açın'
description: Visual Studio ile bir Git veya Azure DevOps deposundaki bir projeyi açmayı öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 11/11/2021
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
ms.openlocfilehash: 619a9cacfdf272bb6b76e0115b90edddf2c73180
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534170"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: bir depodan bir proje açın

bu öğreticide, bir depoya ilk kez bağlanmak ve ardından bir projeyi açmak için Visual Studio kullanacaksınız.

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

    :::image type="content" source="../ide/media/vs-2022/clone-repository-enter-location.png" alt-text="Git deposu URL 'si girdiğiniz Visual Studio bir depoyu kopyala iletişim kutusunun ekran görüntüsü.":::

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

## <a name="browse-to-an-azure-devops-repo"></a>Azure DevOps depoya gidin

Azure DevOps bir depoyu Visual Studio kullanarak nasıl gözataöğreneceksiniz.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Azure DevOps için Visual Studio bir depoyu kopyala iletişim kutusunun ekran görüntüsü.":::

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio Azure DevOps vurgulanmış olan ' depoyu kopyala ' iletişim kutusunun ' bir depoya gözatatıon ' bölümünün ekran görüntüsü.":::

1. aradığınız dosyaları içeren bir Azure DevOps depoyu kopyalamak için istemleri izleyin ve sonra projenizi açın.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile GitHub deposundan proje açma

Visual Studio kullanarak bir projeyi GitHub deposundan açtığınızda, sahip olduğunuz sürüme göre değişir. özellikle, sürüm Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümünü yüklediyseniz, Visual Studio kullanabileceğiniz yeni, daha kapsamlı bir tam olarak tümleşik [Git deneyimi](../version-control/git-with-visual-studio.md) mevcuttur.

ancak, hangi sürümü yüklediğinizden bağımsız olarak bir projeyi Visual Studio GitHub deposundan her zaman açabilirsiniz.

### <a name="visual-studio-2019-version-168-and-later"></a>Visual Studio 2019 sürüm 16,8 ve üzeri

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

### <a name="visual-studio-2019-version-167-and-earlier"></a>Visual Studio 2019 sürüm 16,7 ve öncesi

işte Visual Studio 2019 [**sürüm 16,7**](/visualstudio/releases/2019/release-notes-history) veya önceki sürümlerde Git 'i kullanma.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub depoyu kopyalayın ve ardından bir proje açın

1. Visual Studio 2019 sürüm 16,7 veya öncesini açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluştur ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından **Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' kopya veya kullanıma alma kodu ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio projeden projeyi açar.

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. bunu seçin ve çözümünüzü Visual Studio açar.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Çözüm Gezgini açılan listesinin ekran görüntüsü.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsü "hiçbir çözüm bulunamadı" ifadesini ifade etmez. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

    Kodlamaya başlayın!

## <a name="browse-to-an-azure-devops-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile Azure DevOps depoya gidin

Visual Studio 2019 kullanarak bir Azure DevOps deposuna gözatıp klonladığınızda gördüğünüz özellikler, sahip olduğunuz sürüme bağlıdır. özellikle, sürüm [**16,8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümü yüklediyseniz, kullanıcı arabirimini Visual Studio Visual Studio yeni, daha fazla tümleşik [Git deneyimine](../version-control/git-with-visual-studio.md) uyum sağlayacak şekilde değiştirdik.

ancak hangi sürümü yüklediğinizden bağımsız olarak, Visual Studio Azure DevOps depoya her zaman gidebilirsiniz ve kopyalayabilirsiniz.

### <a name="visual-studio-2019-version-168-and-later"></a>Visual Studio 2019 sürüm 16,8 ve üzeri

1. Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes-history) veya üstünü açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

   ![Azure DevOps için Visual Studio 2019 sürüm 16,8 ve üzeri bir depoyu kopyala iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/clone-repository.png)

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

    ![Visual Studio 2019 sürüm 16,8 ve sonrasında ' Bağlan Project ' iletişim kutusunun ' bir depoya gözatatıon ' bölümünün ekran görüntüsü.](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Bağlan Project ' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > bağlanılacak olan depoların önceden doldurulmuş bir listesini görmüyorsanız sunucu URL 'si girmek için **Azure DevOps Server ekle** ' yi seçin. (alternatif olarak, var olan bir Azure DevOps Server ekleme veya Azure DevOps hesabı oluşturma bağlantıları içeren "sunucu bulunamadı" istemi görebilirsiniz.)

   sonra, Visual Studio klasörleri ve dosyaları gösteren **Çözüm Gezgini** açar.

1. Azure DevOps eylemlerini görüntülemek için **Takım Gezgini** sekmesini seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Takım Gezgini ' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="visual-studio-2019-version-167-and-earlier"></a>Visual Studio 2019 sürüm 16,7 ve öncesi

1. Visual Studio 2019 [**sürüm 16,7**](/visualstudio/releases/2019/release-notes-history) veya öncesini açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluştur ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Azure DevOps listeleyen ' bir depoya göz at ' bölümü ile ' kopyalama veya kullanıma alma kodu ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,7 ve öncesinden oluşturulan ' Bağlan Project ' iletişim kutusunun ekran görüntüsü.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > liste kutusunda gördükleriniz, erişiminizin olduğu Azure DevOps depolarına bağlıdır.

   Visual Studio **Takım Gezgini** açılır ve kopya tamamlandığında bir bildirim belirir.

     ![kopyalama tamamlandıktan sonra, Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin ekran görüntüsü.](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **klasör görünümünü göster** bağlantısını seçin.

     ![kopyalama tamamlandıktan sonra, Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin çözümler bölümünün ekran görüntüsü.](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Gezgini** açılır.

1. Açmak için bir çözüm dosyası (özellikle bir. sln dosyası) aramak üzere **çözümler ve klasörler** bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini ' çözümler ve klasörler ' bildiriminin ekran görüntüsü.](./media/open-proj-repo-solutions-folders.png)

   Deponuzda bir çözüm dosyanız yoksa, ' hiçbir çözüm bulunamadı ' iletisi görüntülenir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2017"></a>Visual Studio 2017 ile GitHub deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda,  >  > **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini Bağlan** bölmesi açılır.

    ![Visual Studio ıde içindeki Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. **Yerel Git depoları** bölümünde, **Kopyala**' yı seçin.

    ![Yerel Git depoları bölümünden kopyayı seçin](./media/open-proj-repo-local-git-repo-clone.png)

1. ***Kopyalanacak bir git deposunun URL 'Sini girin** _, deponuzu URL 'sini yazın veya yapıştırın ve ardından _ * ENTER * * tuşuna basın. (GitHub oturum açmak için bir istem alabilirsiniz; varsa, bunu yapın.)

   deponuzu Visual Studio klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

   ![Çözüm Gezgini "çözümler ve klasörler" i seçin](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. bunu seçin ve çözümünüzü açar Visual Studio.

   ![Çözüm Gezgini açılır listesinden ne açmak istediğinizi seçin.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

   ![GitHub deposunda proje açma animasyonu Visual Studio 2017 ' i kullanarak.](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-with-visual-studio-2017"></a>Visual Studio 2017 ile Azure DevOps deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda,  >  > **kaynak denetiminden** dosya aç aç ' ı seçin.

   **Takım Gezgini Bağlan** bölmesi açılır.

    ![Visual Studio ıde içindeki Takım Gezgini penceresi.](./media/open-proj-repo-team-explorer.png)

1. işte Azure DevOps depoya bağlanmanın iki yolu vardır:

      - **barındırılan hizmet sağlayıcıları** bölümünde **Bağlan..**. seçeneğini belirleyin.

        ![Visual Studio ıde içindeki Takım Gezgini penceresinin barındırılan hizmet sağlayıcıları bölümü.](./media/open-proj-repo-azure-devops.png)

      - **bağlantıları yönet** açılan listesinde **bir Project Bağlan seçin...**

        ![Visual Studio ıde içindeki Takım Gezgini penceresinin bağlantıları yönet bölümü.](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio tarafından oluşturulan ' Bağlan Project ' iletişim kutusu.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > liste kutusunda gördükleriniz, erişiminizin olduğu Azure DevOps depolarına bağlıdır.

1. deponuzu Visual Studio klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

      ![Visual Studio ' deki Takım Gezgini çözüm ve klasörler "bildirimi.](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve klasörler" açılan menüsünde bir çözüm dosyası (özellikle bir. sln dosyası) görüntülenir. bunu seçin ve çözümünüzü açar Visual Studio.

   Deponuzda bir çözüm dosyanız yoksa, giriş menüsünde "hiçbir çözüm bulunamadı" söylecektir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki dile özgü öğreticilerden herhangi birine daha fazla bilgi alabilirsiniz:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript**, **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="<=vs-2019"

- [Visual Studio git deneyimi](../version-control/git-with-visual-studio.md)
- [Git ve Takım Gezgini yan yana karşılaştırın](../version-control/git-team-explorer-feature-comparison.md)
- [Microsoft Learn: Visual Studio Git ve GitHub kullanmaya başlama](/learn/modules/visual-studio-github-push/)
- [Microsoft Learn: Azure DevOps kullanmaya başlama](/learn/modules/get-started-with-devops/)
- [Azure DevOps Services: Azure Repos ve Visual Studio kullanmaya başlayın](/azure/devops/repos/git/gitquickstart/)

::: moniker-end

::: moniker range="vs-2022"

[sürüm denetimi belgelerini Visual Studio](../version-control/index.yml)

::: moniker-end