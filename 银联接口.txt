interface UnionPay
{
	public void detect();//检测密码
	public void withdraw();//取钱
	public void balance();//查询余额
}
class ATM
{
	public void plugin(UnionPay up){
		up.detect();
		up.withdraw();
		up.balance();
	}
}
class ICBC implements UnionPay{
	private double comm;
	private double pay;
	public ICBC (double comm,double pay){
		this.comm=comm;
		this.pay=pay;
	}
	public void setComm(double comm){
		this.comm=comm;
	}
	public void setPay(double pay){
		this.pay=pay;
	}
	public double getComm(){
		return this.pay;
	}
	public double getPay(){
		return this.pay;
	}
	public void detect(){
		System.out.println("正在工商银行检测密码...");
	}
    public void withdraw(){
		System.out.println("正在工商银行取钱...");
		this.comm-=pay;
		if(this.comm<=0){
			System.out.println("余额不足...");
			comm+=pay;
		}
		else
			System.out.println("成功取款"+this.pay+"元");
	}
    public void balance(){
		if(this.comm>=0)
		System.out.println("查询余额为"+this.comm+"元");
		else
			System.out.println("查询余额为0元");
	}
	public void payonline(){
		System.out.println("进行在线支付...");
		this.comm-=pay;
		if(this.comm<=0){
			System.out.println("余额不足...");
			comm+=pay;
		}
		else
			System.out.println("成功支付"+this.pay+"元");
	}
}
class ABC implements UnionPay{
    private double comm;
	private double pay;
	public ABC (double comm,double pay){
		this.comm=comm;
		this.pay=pay;
	}
	public void setComm(double comm){
		this.comm=comm;
	}
	public void setPay(double pay){
		this.pay=pay;
	}
	public double getComm(){
		return this.pay;
	}
	public double getPay(){
		return this.pay;
	}
	public void detect(){
		System.out.println("正在农业银行检测密码...");
	}
    public void withdraw(){
		System.out.println("正在农业银行取钱...");
		this.comm-=pay;
		if(this.comm<-2000){
			System.out.println("最多透支2000元，超出透支。");
			comm+=pay;
		}
		else
			System.out.println("成功取款"+this.pay+"元");
	}
    public void balance(){
		if(this.comm>=0)
		System.out.println("查询余额为"+this.comm+"元");
		else
			System.out.println("透支"+this.comm+"元");
	}
	public void payphonebill(){
		System.out.println("正在支付电话费...");
		this.comm-=pay;
		if(this.comm<-2000){
			System.out.println("最多透支2000元，超出透支。");
			comm+=pay;
		}
		else
			System.out.println("成功支付"+this.pay+"元");
	}
}
public class TestDemo61
{
	public static void main(String args[]){
		ATM atm=new ATM();
        ICBC icbc=new ICBC(20000,3000);
        ABC abc=new ABC(2000,2000);
		atm.plugin(icbc);
		icbc.payonline();
        icbc.balance();
		System.out.println("--------------");
        atm.plugin(abc);
		abc.payphonebill();
		abc.balance();
	}
}