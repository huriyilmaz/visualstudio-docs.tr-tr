---
title: Sözde değişkenler | Microsoft Docs
description: Visual Studio hata ayıklayıcısında sahte değişkenleri gözden geçirin. Sözde değişkenler, belirli verileri bir değişken penceresinde veya QuickWatch iletişim kutusunda göstermek için kullanılan terimlerdir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88880110ca00141382d7038ec001f3cc4159f2b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908335"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında sahte değişkenler
Sözde değişkenler, belirli bilgileri bir değişken penceresinde veya **QuickWatch** iletişim kutusunda göstermek için kullanılan terimlerdir. Bir sözde değişkeni, normal bir değişkene girebileceğiniz şekilde girebilirsiniz. Ancak sözde değişkenler, değişken değildir ve programınızdaki değişken adlarına karşılık gelmez.

## <a name="example"></a>Örnek
 Bir yerel kod uygulaması yazdığınızı ve uygulamanızda ayrılan tanıtıcı sayısını görmek istediğinizi varsayalım. **Gözcü** penceresinde, **ad** sütununa aşağıdaki sözde değişkeni girebilir ve sonra değerlendirmek için Return tuşuna basabilirsiniz:

`$handles`

 Yerel kodda, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:

|Sözde değişken|İşlev|
|--------------------|--------------|
|`$err`|SetLastError işleviyle birlikte ayarlanan son hata değerini görüntüler. Görüntülenen değer, GetLastError işlevinin ne döndürüleceğini gösterir.<br /><br /> `$err,hr`Bu değerin kodu çözülmüş biçimini görmek için kullanın. Örneğin, son hata 3 ise, şu şekilde `$err,hr` görüntülenir `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Uygulamanızda ayrılan tanıtıcı sayısını görüntüler.|
|`$vframe`|Geçerli yığın çerçevesinin adresini görüntüler.|
|`$tid`|Geçerli iş parçacığının iş parçacığı KIMLIĞINI görüntüler.|
|`$env`|Dize görüntüleyicisinde ortam bloğunu görüntüler.|
|`$cmdline`|Programı başlatan komut satırı dizesini görüntüler.|
|`$pid`|İşlem KIMLIĞINI görüntüler.|
|`$`*RegisterName*<br /><br /> veya<br /><br /> `@`*RegisterName*|Kayıt *RegisterName*'in içeriğini görüntüler.<br /><br /> Normalde kayıt adını girerek kayıt içeriğini görüntüleyebilirsiniz. Bu söz dizimini kullanmanız gereken tek zaman, YAZMAÇ adının bir değişken adını aşırı yükleyidir. Kayıt adı, geçerli kapsamdaki bir değişken adıyla aynıysa, hata ayıklayıcı adı değişken adı olarak yorumlar. Bu, `$` *RegisterName* veya `@` *RegisterName* yararlı olarak sunulur.|
|`$clk`|Saat döngülerinde saati görüntüler.|
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgilerine sahip bir yapı görüntüler. Güvenlik nedenleriyle parola bilgileri gösterilmez.|
|`$exceptionstack`|Geçerli Windows Çalışma Zamanı özel durumunun yığın izlemesini görüntüler. `$ exceptionstack` yalnızca UWP uygulamalarında işe yarar. `$ exceptionstack` C++ ve SEH özel durumları için desteklenmez|
|`$returnvalue`|Bir yöntemin dönüş değerini görüntüler.|

 C# ' de, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:

|Sözde değişken|İşlev|
|--------------------|--------------|
|`$exception`|Son özel durum hakkındaki bilgileri görüntüler. Bir özel durum oluştuysa, değerlendirmek `$exception` bir hata mesajı görüntüler.<br /><br /> Özel durum Yardımcısı devre dışı bırakıldığında, `$exception` bir özel durum oluştuğunda **Yereller** penceresine otomatik olarak eklenir.|
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgilerine sahip bir yapı görüntüler. Güvenlik nedenleriyle parola bilgileri gösterilmez.|
|`$returnvalue`|Bir .NET yönteminin dönüş değerini görüntüler.|

 Visual Basic, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:

|Sözde değişken|İşlev|
|--------------------|--------------|
|`$exception`|Son özel durum hakkındaki bilgileri görüntüler. Bir özel durum oluştuysa, değerlendirmek `$exception` bir hata mesajı görüntüler.|
|`$delete` veya `$$delete`|**Komut** penceresinde oluşturulan örtük bir değişkeni siler. Söz dizimi `$delete,` *değişken* veya `$delete,` *değişkendir*`.`|
|`$objectids` veya `$listobjectids`|Tüm etkin nesne kimliklerini belirtilen ifadenin alt öğesi olarak görüntüler. Söz dizimi `$objectid,` *ifade* veya `$listobjectids,` *ifadedir*`.`|
|`$`*N*`#`|Nesne KIMLIĞIYLE birlikte *N* değerine eşit olan nesneyi görüntüler.|
|`$dynamic`|Uygulayan bir nesne için özel **Dinamik görünüm** düğümünü görüntüler `IDynamicMetaObjectProvider` . Arayüz. Sözdizimi `$dynamic,` *Object*. Bu özellik yalnızca .NET Framework sürüm 4 veya üstünü kullanan kod için geçerlidir.|

## <a name="see-also"></a>Ayrıca bkz.
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Değişken pencereleri](../debugger/debugger-windows.md)
