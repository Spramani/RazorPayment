# RazorPayment
razorPayment_iOS


pod install
   # Pods for RazorPayment
	pod 'razorpay-pod', '~> 1.1.12'
 





import UIKit
import Razorpay



class ViewController: UIViewController, RazorpayPaymentCompletionProtocol {
    
    //    typealias Razorpay = RazorpayCheckout
   var razorpay: RazorpayCheckout!
   
   override func viewDidLoad() {
        super.viewDidLoad()
        razorpay = RazorpayCheckout.initWithKey("rzp_test_uHC5h08RtxnxP1", andDelegate: self)     
    }
    
   override func viewWillAppear(_ animated: Bool) {
   
        super.viewWillAppear(animated)
        self.showPaymentForm()    
    }
    
    
    //action event
    
   @IBAction func processpay(_ sender: UIButton)    
   
        showPaymentForm()
    }
    
    
   func onPaymentError(_ code: Int32, description str: String) {
  
        let alert = UIAlertController(title: "Failure", message: str, preferredStyle: .alert)
        let cancel = UIAlertAction(title: "cancel", style: .cancel, handler: nil)
        alert.addAction(cancel)
        self.view.window?.rootViewController?.present(alert, animated: true, completion: nil)
    }
    
    
   func onPaymentSuccess(_ payment_id: String) {
   
        let alert = UIAlertController(title: "Success", message: payment_id, preferredStyle: .alert)
        let cancel = UIAlertAction(title: "ok", style: .cancel, handler: nil)
        alert.addAction(cancel)
        self.view.window?.rootViewController?.present(alert, animated: true, completion: nil)
    }
    
    
   internal func showPaymentForm(){
   
        let options: [String:Any] = [
            "amount": "152000", //This is in currency subunits.100 = 100 paise= INR 1.
            "description": "purchase description",
            "image": "imageurl",
            "name": "business or product name",
            "prefill": [
                "contact": "9898989898",
                "email": "shubhamramani@gmail.com"
            ],
            "theme": [
                "color": "#F37254"
            ]
        ]
        razorpay.open(options)}
    
}


<a href="https://ibb.co/CQW2Y62"><img src="https://i.ibb.co/rHvsz3s/Simulator-Screen-Shot-i-Phone-11-2021-04-13-at-18-33-26.png" alt="Simulator-Screen-Shot-i-Phone-11-2021-04-13-at-18-33-26" border="0"></a>
