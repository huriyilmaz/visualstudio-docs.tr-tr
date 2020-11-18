---
title: Visual Studio’da GitHub hesaplarıyla çalışma
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Visual Studio 'Yu GitHub hesaplarıyla nasıl kullanacağınızı öğrenin.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 845b663a3a0828806766fa0609e45efafabec50a
ms.sourcegitcommit: e8a13978131f257d91ce37c5a2e0d153a4c400ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704031"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Visual Studio’da GitHub hesaplarıyla çalışma

Ortak bir GitHub veya GitHub Enterprise hesabınız varsa, Visual Studio anahtarınıza ekleyebilirsiniz. Hesabınızı ekledikten sonra, doğrudan Visual Studio 'dan GitHub depolarına erişerek ve oluşturarak platform tümleştirmesinden yararlanabilirsiniz.

## <a name="adding-public-github-accounts"></a>Ortak GitHub hesapları ekleme

Visual Studio 'da bir Microsoft hesabı veya bir iş veya okul hesabı ile zaten oturum açtıysanız, genel GitHub hesabınızı ekleyebilirsiniz.

1. Visual Studio ortamının sağ üst köşesindeki baş harflerinizi içeren simgeyi seçin. Ardından, hesaplarınızı yönetmek için **Hesap ayarları...** seçeneğini belirleyin. Ayrıca, **Dosya**  >  **hesabı ayarları**' na giderek hesap ayarları iletişim kutusunu açabilirsiniz.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Hesap ayarları":::

2. **Tüm hesaplar** alt menüsünde, hesap eklemek için artı işaretini seçin ve **GitHub**' ı seçin.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="GitHub hesabı ekle 'yi seçin":::

3. Tarayıcıya yönlendirilirsiniz, burada GitHub kimlik bilgilerinizle oturum açabilirsiniz. Oturum açtıktan sonra, tarayıcıda başarılı bir pencere alırsınız ve Visual Studio 'ya geri dönebilirsiniz.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Tarayıcıda başarı penceresi":::

4. Her iki hesabınız de **tüm hesaplar** alt menüsünde bulunur.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Her iki hesap de gösteriliyor":::

Visual Studio 'da farklı bir hesapla oturum açmadıysanız, Visual Studio ortamının sağ üst köşesindeki **oturum aç** bağlantısını seçin. Ayrıca, **Dosya**  >  **hesabı ayarları**' na giderek hesap ayarları iletişim kutusunu açabilirsiniz. Ardından, GitHub hesabınızı eklemek için yukarıdaki yönergeleri izleyin.

![Oturum açmamış Kullanıcı](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>GitHub Enterprise hesapları ekleme

Varsayılan olarak, Visual Studio 'Nun yalnızca genel GitHub hesapları etkindir.

1. GitHub Enterprise hesaplarını etkinleştirmek için, **Araçlar**  >  **Seçenekler** ' e gidin ve **hesaplar** seçeneklerini arayın.

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Hesap seçenekleri menüsü":::

2. Daha sonra, **GitHub Enterprise Server hesaplarını dahil** etmek için kutuyu işaretleyin. **Hesap ayarlarınıza** bir dahaki sefer gittiğinizde GitHub hesabı eklemeye çalıştığınızda hem GitHub hem de GitHub Enterprise seçeneklerini görürsünüz.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="GitHub Enterprise ile oturum açma":::

3. GitHub Enterprise Server adresinizi girdikten sonra **tarayıcınızla oturum aç**' ı seçin. Burada, GitHub kurumsal kimlik bilgilerinizi kullanarak oturum açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok kullanıcı hesabıyla çalışma](work-with-multiple-user-accounts.md)
- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
