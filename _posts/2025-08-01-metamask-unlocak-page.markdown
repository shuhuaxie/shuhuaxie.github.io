- 登录界面ui 
	- ui/pages/unlock-page/
	- Mascot 小狐狸动画
- 登录的逻辑
	- 登录跳转 DEFAULT_ROUTE  'Home'
	- ui/store/action.ts
		(resolve, reject) => {
      		callBackgroundMethod(
        		'syncPasswordAndUnlockWallet',
       		 [password],
       		 (error, isPasswordSynced) => {
       		   if (error) {
       		     	reject(error);
       		     	return;
        		  }
        		  // if password is not synced show connections removal warning to user.
       		   if (!isPasswordSynced) {
        		    dispatch(setShowConnectionsRemovedModal(true));
       		   }
       		   resolve();
      		  },
    		  );
  		  }
  	- BackgroundRpcClient
  	- app/scripts/ui.js
  		- browser.runtime.connect
  	- app/scripts/background.js
  		- browser.runtime.onConnect.addListener
  	- app/scripts/metamask-controller.js
  	- core | packages/keyring-controller/src/KeyringController.ts - submitPassword
- 技术
	- redux
		- store
			- getState 获取当前状态
		- reducer
		- useSelector
		- dispatch
		- compose
			组件层层合并（固定先withRouter，后connect）
				compose(
  					withRouter,
  					connect(mapStateToProps, mapDispatchToProps, mergeProps),
				)(UnlockPage);
	- react-redux
		- connect
			const connect = (a, b, c) => {
  				// 返回一个"连接器"函数，接收原始数据
  				return (dataA, dataB) => {
    				const outputA = a(dataA); // 先用第一个函数处理dataA
    				const outputB = b(dataB); // 再用第二个函数处理dataB
    				return c(outputA, outputB); // 最后用第三个函数合并结果
  				};
			};
	- react-router-dom 
		- 作用
			- 定义页面路由
			- 页面跳转和传参
			- 页面嵌套
		- https://v5.reactrouter.com/
		- withRouter
		- 默认路由 path="/"
		- 首页 ui/index.js
			- _base.json
				- "background": {
    				"page": "background.html",
    				"persistent": true
  					},
  						- 事件驱动而非持续运行
  				- "background": {
    					"service_worker": "scripts/app-init.js"
  					},
				- "default_popup": "popup-init.html"
					- url=/popup.html
						- popup.html    
							- app-content
				- ui.js
					- launchMetaMaskUi	
				- ui/index.js
				- render(<Root store={store} />, opts.container)
				- ui/pages/index.js
				- Routes
				- routes.container.js
				- routes.component.js
	
	- CORS限制
	- 显示余额
	- 转账
	- 签名
	
	
	