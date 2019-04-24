# Intent

https://github.com/7419adf/Intent/blob/master/images/%E5%AE%9E%E9%AA%8C%E4%BA%94.1.png
https://github.com/7419adf/Intent/blob/master/images/%E5%AE%9E%E9%AA%8C%E4%BA%94.2.png
https://github.com/7419adf/Intent/blob/master/images/%E5%AE%9E%E9%AA%8C%E4%BA%94.3.png

 protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button btn = (Button)findViewById(R.id.button);//获取按钮
        btn.setOnClickListener(new View.OnClickListener() {       //设置按钮单击事件
            @Override
            public void onClick(View v) {

                EditText et = (EditText)findViewById(R.id.editText);//获取edittext组件
                String cn = et.getText().toString();//获取edittext中填写的内容
                //  Uri uri = Uri.parse(cn);

                Intent intent = new Intent();
                intent.setAction("android.intent.action.VIEW");

                //  intent.setClassName("com.android.browser","com.android.browser.BrowserActivity");
                //  intent.setClassName("com.example.mybrowser","com.example.mybrowser.MainActivity");
                Bundle bundle = new Bundle();
                bundle.putString("address",cn);
                intent.putExtras(bundle);

                Intent chooser = Intent.createChooser(intent, "请选择以下应用打开");
                if (intent.resolveActivity(getPackageManager()) != null) {
                    startActivity(intent);
                }


            }
        });

    }
