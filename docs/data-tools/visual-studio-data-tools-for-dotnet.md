---
title: .NET için veri araçları
description: veritabanlarına bağlanmak, bellekteki verileri modellemek ve kullanıcı arabirimindeki verileri göstermek için apı ve araç desteği sağlayan .net için Visual Studio veri araçlarını gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: adf70d81747cfee833c996acaaecf6b1009f6fed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031555"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET için Visual Studio veri araçları

Visual Studio ve .net birlikte, veritabanlarına bağlanmak, bellekteki verileri modellemesi ve kullanıcı arabirimindeki verileri görüntülemek için kapsamlı apı ve araç desteği sağlar. Veri erişim işlevselliği sağlayan .NET sınıfları [ADO.net](/dotnet/framework/data/adonet/index)olarak bilinir. ADO.NET, Visual Studio veri araçlarının yanı sıra ilişkisel veritabanlarını ve XML 'yi destekleyecek şekilde tasarlanmıştır. bu günler, birçok nosql veritabanı satıcısı veya üçüncü taraf, ADO.NET sağlayıcıları sunmaktadır.

[.net Core](/dotnet/core/) , veri kümeleri ve bunlarla ilgili türler hariç ADO.NET destekler. .NET Core 'u hedefliyorsanız ve nesne ilişkisel eşleme (ORM) katmanı gerektiriyorsa, [Entity Framework Core](/ef/core/)kullanın.

Aşağıdaki diyagramda temel mimarinin basitleştirilmiş bir görünümü gösterilmektedir:

![ADO.NET Mimarisi](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Tipik iş akışı

Tipik iş akışı budur:

1. Yerel makinenize bir geliştirme veya test veritabanı yükler. Bkz. [veritabanı sistemlerini, araçları ve örnekleri yükleme](../data-tools/installing-database-systems-tools-and-samples.md). Azure Data Service kullanıyorsanız, bu adım gerekli değildir.

2. Visual Studio ' deki veritabanı (veya hizmet ya da yerel dosya) bağlantısını test edin. Bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. Seçim Yeni bir model oluşturmak ve yapılandırmak için araçları kullanın. Entity Framework göre modeller, yeni uygulamalar için varsayılan önersahiptir. Kullandığınız bir model, uygulamanın etkileşime girdiği veri kaynağıdır. Model, veritabanı veya hizmet ile uygulama arasında mantıksal olarak bulunur. Bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

4. verileri belirttiğiniz şekilde kullanıcıya görüntüleyecek veri bağlama kodunu oluşturmak için veri **kaynakları** penceresinden bir Windows Forms, ASP.NET veya Windows Presentation Foundation tasarım yüzeyine sürükleyin. Bkz. [Visual Studio verileri denetimlere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. İş kuralları, arama ve veri doğrulama gibi şeyler için veya temeldeki veritabanının sunduğu özel işlevlerden faydalanmak için özel kod ekleyin.

Bir model kullanmak yerine, komutları doğrudan bir veritabanına vermek için adım 3 ' ü ve bir .NET uygulamasını programlayabilirsiniz. Bu durumda, ilgili belgeleri buradan bulabilirsiniz: [ADO.net](/dotnet/framework/data/adonet/index). Veri **kaynağı Yapılandırma Sihirbazı 'nı** ve tasarımcılarını bellekte kendi nesnelerinizi doldurduktan sonra veri bağlama kodu oluşturmak için de kullanabileceğinizi ve bu nesnelere veri bağlamayı unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
