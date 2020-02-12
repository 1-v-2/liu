# liu
WindowManager wm = (WindowManager) context.getSystemService(Context.WINDOW_SERVICE);
WindowManager.LayoutParams params = new WindowManager.LayoutParams();
params.type = WindowManager.LayoutParams.TYPE_SYSTEM_ALERT;
params.format = PixelFormat.RGBA_8888;
params.flags = WindowManager.LayoutParams.FLAG_NOT_TOUCH_MODAL
      | WindowManager.LayoutParams.FLAG_NOT_FOCUSABLE;
params.width = petW;
params.height = petW;
params.x = 0;
params.y = 0;
elfView.setVisibility(VISIBLE);
wm.addView(elfView, params);
params.x =dx;
params.y = dy;
wm.updateViewLayout(elfView, params);
case MotionEvent.ACTION_DOWN:
   lastX = (int) event.getRawX();
   lastY = (int) event.getRawY();
   paramX = params.x;
   paramY = params.y;
   break;
case MotionEvent.ACTION_MOVE:
   dx = (int) event.getRawX() - lastX;
   dy = (int) event.getRawY() - lastY;
   params.x = paramX + dx;
   params.y = paramY + dy;
   wm.updateViewLayout(elfView, params);
   break;
