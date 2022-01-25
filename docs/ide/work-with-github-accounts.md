---
title: Visual Studio’da GitHub hesaplarıyla çalışma
ms.date: 11/16/2020
ms.custom: ''
ms.topic: how-to
description: Visual Studio GitHub hesaplarıyla nasıl kullanacağınızı öğrenin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: f03b494c688fa9ac232175366e59e1740258d37f
ms.sourcegitcommit: 429b2378ee21b5f473b26f4b4ea0a70372a34ec2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "137733394"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Visual Studio’da GitHub hesaplarıyla çalışma

ortak bir GitHub veya GitHub Enterprise hesabınız varsa, Visual Studio anahtarınıza ekleyebilirsiniz. hesabınızı ekledikten sonra, Visual Studio doğrudan GitHub depolarına erişerek ve oluşturarak platform tümleştirmesinden yararlanabilirsiniz.

## <a name="adding-public-github-accounts"></a>ortak GitHub hesapları ekleme

zaten bir Microsoft hesabı veya bir iş veya okul hesabı ile Visual Studio oturum açtıysanız genel GitHub hesabınızı ekleyebilirsiniz.

1. Visual Studio ortamının sağ üst köşesindeki baş harflerinizi içeren simgeyi seçin. Ardından, hesaplarınızı yönetmek için **Hesap ayarları...** seçeneğini belirleyin. ayrıca, Ayarlar **dosya** hesabı ' na giderek hesap Ayarlar iletişim kutusunu açabilirsiniz  >  .

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Hesap ayarları":::

2. **Tüm hesaplar** alt menüsünde, hesap eklemek için artı işaretini seçin ve **GitHub**' yi seçin.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="GitHub hesap ekle ' yi seçin":::

3. tarayıcıya yönlendirilirsiniz, burada GitHub kimlik bilgilerinizle oturum açabilirsiniz. Oturum açtıktan sonra, tarayıcıda başarılı bir pencere alırsınız ve Visual Studio geri dönebilirsiniz.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Tarayıcıda başarı penceresi":::

4. Her iki hesabınız de **tüm hesaplar** alt menüsünde bulunur.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Her iki hesap de gösteriliyor":::

farklı bir hesapla Visual Studio üzere oturum açmadıysanız, Visual Studio ortamının sağ üst köşesindeki **oturum aç** bağlantısını seçin. ayrıca, Ayarlar **dosya** hesabı ' na giderek hesap Ayarlar iletişim kutusunu açabilirsiniz  >  . ardından, GitHub hesabınızı eklemek için yukarıdaki yönergeleri izleyin.

![Oturum açmamış Kullanıcı](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-managed-user-emu-accounts"></a>GitHub Enterprise yönetilen kullanıcı (EMU) hesapları ekleme

zaten bir Microsoft hesabı veya bir iş veya okul hesabı ile Visual Studio oturum açtıysanız GitHub EMU hesabınızı ekleyebilirsiniz.

1. Visual Studio ortamının sağ üst köşesindeki baş harflerinizi içeren simgeyi seçin. Ardından, hesaplarınızı yönetmek için **Hesap ayarları...** seçeneğini belirleyin. ayrıca, Ayarlar **dosya**  >  **hesabına** giderek hesap Ayarlar iletişim kutusunu açabilirsiniz...

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Hesap ayarları iletişim kutusunu gösteren ekran görüntüsü":::

2. **Tüm hesaplar** alt menüsünde, **+** hesap eklemek için veya açılan menü **Ekle** ' yi seçin ve ardından **GitHub**' yi seçin.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="GitHub hesabı seçme ve ekleme işlemlerinin gösterildiği ekran görüntüsü":::

3. GitHub EMU kimlik bilgilerinizle oturum açabileceğiniz tarayıcıya yönlendirilirsiniz. 

> [!NOTE]
> bu sayfada GitHub EMU hesabı kimlik bilgilerinizi (kullanıcı adının bir alt çizgi ve ardından şirket adıyla) girdiğinizden emin olun.

 :::image type="content" source="../ide/media/github-enterprise-managed-users-sign-in.png" alt-text="GitHub Enterprise yönetilen kullanıcı hesabı için GitHub oturum açma deneyimini gösteren ekran görüntüsü":::

Oturum açtıktan sonra, tarayıcıda başarılı bir pencere alırsınız ve Visual Studio geri dönebilirsiniz.

:::image type="content" source="../ide/media/github-success-signin.png" alt-text="Tarayıcıda oturum açma başarısını gösteren ekran görüntüsü":::

## <a name="adding-github-enterprise-accounts"></a>GitHub kurumsal hesap ekleme

varsayılan olarak Visual Studio yalnızca ortak GitHub hesapları etkindir.

1. GitHub kurumsal hesapları etkinleştirmek için **araçlar**  >  **seçenekler** ' e gidin ve **hesaplar** seçeneklerini arayın.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Hesap seçenekleri menüsü":::

2. ardından, **GitHub Enterprise sunucu hesaplarını dahil** etmek için kutuyu işaretleyin. **hesap Ayarlar** bir sonraki sefer ve bir GitHub hesabı eklemeye çalıştığınızda, hem GitHub hem de GitHub Enterprise seçeneklerini görürsünüz.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="GitHub Enterprise ile oturum açın":::

3. GitHub Enterprise sunucu adresinizi girdikten sonra **tarayıcınızla oturum aç**' ı seçin. burada, GitHub Enterprise kimlik bilgilerinizi kullanarak oturum açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok kullanıcı hesabıyla çalışma](work-with-multiple-user-accounts.md)
- [Visual Studio oturum açın](signing-in-to-visual-studio.md)
