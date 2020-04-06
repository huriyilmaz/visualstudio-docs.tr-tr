---
title: SccCreateSubProject Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701032"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject fonksiyonu
Bu işlev, `lpParentProjPath` bağımsız değişken tarafından belirtilen varolan bir üst proje altında verilen adı içeren bir alt proje oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpUser

[içinde, dışarı] Kullanıcı adı (NULL sonlandırıcı dahil olmak üzere en SCC_USER_SIZE).

 lpParentProjPath

[içinde] Ana projenin yolunu tanımlayan bir dize (NULL sonlandırıcıdahil SCC_PRJPATH_SIZE kadar).

 lpSubProjName

[içinde] Önerilen alt proje adı (NULL sonlandırıcısı da dahil olmak üzere SCC_PRJPATH_SIZE kadar).

 lpAuxProjPath

[içinde, dışarı] Projeyi tanımlayan yardımcı dize (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpSubProjPath

[içinde, dışarı] Alt proje yolunu tanımlayan çıkış dizesi (NULL sonlandırıcıdahil SCC_PRJPATH_SIZE kadar).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Alt proje başarıyla oluşturuldu.|
|SCC_E_INITIALIZEFAILED|Üst proje başharfe alınamadı.|
|SCC_E_INVALIDUSER|Kullanıcı kaynak denetim sistemine giriş yapamadı.|
|SCC_E_COULDNOTCREATEPROJECT|Alt proje oluşturulamıyor.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_UNKNOWNPROJECT|Ana proje kaynak denetim eklentisi için bilinmiyor.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamaz dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_CONNECTIONFAILURE|Bir kaynak denetimi eklentisi bağlantı sorunu vardı.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Adı olan bir alt proje zaten varsa, işlev varsayılan adı benzersiz bir ad oluşturmak\<için değiştirebilir, örneğin ona "_ sayısı>" ekleyerek. Arayan, `lpUser`'ve `lpSubProjPath` `lpAuxProjPath`. Ve `lpSubProjPath` `lpAuxProjPath` bağımsız değişkenler daha sonra [SccOpenProject'e](../extensibility/sccopenproject-function.md)yapılan bir çağrıda kullanılır. Bunlar döndükten sonra arayan tarafından değiştirilmemelidir. Bu dizeleri, kaynak denetim eklentisinin projeyle ilişkilendirmesi gereken bilgileri izlemesi için bir yol sağlar. Eklenti görüntüleme için uygun olmayabilir biçimlendirilmiş bir dize kullanabilirsiniz, çünkü arayan IDE, döndükten sonra bu iki parametre görüntüleme olmaz. İşlev bir başarı veya hata kodu döndürür `lpSubProjPath` ve başarılı olursa, değişkeni yeni projeye giden tam proje yolu ile doldurur.

 Bu işlev [SccGetProjPath](../extensibility/sccgetprojpath-function.md)benzer , sessizce yerine birini seçmek için kullanıcı isteyen bir proje oluşturur dışında. `SccCreateSubProject` İşlev çağrıldığında `lpParentProjName` `lpAuxProjPath` ve boş olmayacak ve geçerli bir projeye karşılık gelecektir. Bu dizeleri genellikle `SccGetProjPath` ide tarafından önceki bir çağrıdan fonksiyona veya [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)alınır.

 `lpUser` Bağımsız değişken kullanıcı adıdır. IDE, daha önce aldığı `SccGetProjPath`kullanıcı adı ile geçer ve kaynak denetim eklentisi varsayılan olarak adı kullanmalıdır. Kullanıcının eklentiyle zaten açık bir bağlantısı varsa, eklenti işlevin sessizce çalıştığından emin olmak için herhangi bir istemleri ortadan kaldırmaya çalışmalıdır. Ancak, oturum açma başarısız olursa, eklenti kullanıcıdan oturum açma için istekte olmalı ve geçerli bir giriş `lpUser`aldığında adı 'ne geri geçirin. Eklenti bu dizeyi değiştirebileceğinden, IDE her zaman null terminator için alan içeren bir boyut arabelleği (SCC_USER_LEN+1 veya SCC_USER_SIZE) ayırır. Dize değiştirilirse, yeni dize geçerli bir giriş adı olmalıdır (en azından eski dize kadar geçerlidir).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject ve SccGetParentProjectPath için teknik notlar
 Kaynak denetimine çözüm ve proje ekleme, bir kullanıcıdan kaynak denetim sistemindeki konumları seçme sini en aza indirmek için Visual Studio'da basitleştirilmiştir. Bir kaynak kontrol eklentisi her iki yeni işlevi de destekliyorsa, `SccCreateSubProject` bu değişiklikler Visual Studio tarafından etkinleştirilir ve `SccGetParentProjectPath`. Ancak, aşağıdaki kayıt defteri girişi bu değişiklikleri devre dışı bırakıp önceki Visual Studio'ya (Kaynak Denetimi Eklentisi API Sürüm 1.1) davranışına geri dönmek için kullanılabilir:

 **[HKEY_CURRENT_USER\Yazılım\Microsoft\VisualStudio\8.0\Kaynak Denetimi] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Bu kayıt defteri girişi yoksa veya dword:00000000 olarak ayarlanmışsa, Visual `SccCreateSubProject` Studio `SccGetParentProjectPath`yeni işlevleri kullanmaya çalışır ve .

 Kayıt defteri girişi dword:00000001 olarak ayarlanmışsa, Visual Studio bu yeni işlevleri ve Visual Studio'nun önceki sürümlerinde olduğu gibi kaynak denetimi çalışmasına ekleme işlemlerini kullanmaya çalışmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
