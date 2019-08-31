## laravel 七牛CDN开发者SDK

###安装步骤

使用命令

composer require ladimin/qiniu dev-master

或

composer.json中加入

"require":{

    ...

    "ladimin/qiniu": "dev-master"

}

运行composer install 即可安装

引用例子:

namespace App\Http\Controllers;

use ...;

use Qiniu;

class testController extends Controller{

    public function index()

    {

        $accessKey = '888888';

        $secretKey = '888888';

        $auth=new Qiniu\Auth($accessKey,$secretKey);

        $bucket="test";

        $upToken=$auth->uploadToken($bucket);

        echo $upToken;//获取上传token

        $bucketMgr=new Qiniu\Storage\BucketManager($auth);

        list($iterms,$market,$err)=$bucketMgr->listFiles($bucket); //获取已上传列表

        print_r($iterms);

    }

}

[packagist.org](https://packagist.org/packages/ladimin/qiniu)

## License

The Laravel framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).