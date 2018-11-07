# ElementsProgramactlly,

//
//  ViewController.swift
//  ElementsProgramactlly

//  Creating Constraints with Layout Anchors

//  Created by dmorenoar on 7/11/18.
//  Copyright © 2018 DAM. All rights reserved.
/* https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/LayoutUsingStackViews.html#//apple_ref/doc/uid/TP40010853-CH11-SW1 */

import UIKit

class ViewController: UIViewController {

    
    var imgView: UIImageView = {
        let imagen:UIImage = UIImage(named: "user")!
        let imgView:UIImageView = UIImageView(image: imagen)
        imgView.frame = CGRect(x: 0, y: 0, width: 100, height: 100)
        imgView.layer.cornerRadius = 25
        imgView.layer.borderColor = UIColor.black.cgColor
        imgView.layer.borderWidth = 2
        imgView.clipsToBounds = true
        imgView.contentMode = .scaleAspectFit
        //imgView.sizeThatFits(CGSize(width: 20, height: 20))
        imgView.translatesAutoresizingMaskIntoConstraints = false
        imgView.backgroundColor = UIColor.cyan
        return imgView
    }()
    
    
    var lblTitle:UILabel = {
        let lbl = UILabel()
        lbl.text = "Variable"
        lbl.font = UIFont.systemFont(ofSize: 28)
        lbl.textColor = UIColor.black
        lbl.backgroundColor = UIColor.blue
        lbl.translatesAutoresizingMaskIntoConstraints = false
        lbl.textAlignment = .center
        return lbl
    }()
    
    var btnClick:UIButton = {
        let btn = UIButton(frame: CGRect(x: 100, y: 100, width: 100, height: 100))
        btn.setTitle("Clickame", for: .normal)
        btn.backgroundColor = UIColor.black
        btn.addTarget(self, action: #selector(clicame), for: .touchUpInside)
        btn.translatesAutoresizingMaskIntoConstraints = false
        btn.layer.cornerRadius = 40
        
        return btn
    }()
    
    @objc func clicame() {
        lblTitle.text = "Has pulstado el botón"
    }
    
    
    var containerView:UIView = {
        let containerView:UIView = UIView()
        containerView.translatesAutoresizingMaskIntoConstraints = false
        containerView.backgroundColor = UIColor.brown
        return containerView
    }()
    
    
    
    func setupViews(){
        self.view.addSubview(lblTitle)
        self.view.addSubview(btnClick)
        
        self.view.addSubview(containerView)
        
        containerView.addSubview(imgView)
        
        /*CONTRAINST CONTANIER*/
        containerView.centerXAnchor.constraint(equalTo: view.centerXAnchor).isActive = true
        containerView.topAnchor.constraint(equalTo: view.topAnchor).isActive = true
        //containerView.widthAnchor.constraint(equalToConstant: 20).isActive = true
        containerView.bottomAnchor.constraint(equalTo: view.bottomAnchor).isActive = true
        //containerView.heightAnchor.constraint(equalToConstant: 20).isActive = true
        
        
        
        
        
        //CenterXAnchor
        lblTitle.centerXAnchor.constraint(equalTo: view.centerXAnchor).isActive = true
        //CenterYAnchor
        lblTitle.centerYAnchor.constraint(equalTo: view.centerYAnchor).isActive = true
        
        btnClick.topAnchor.constraint(equalTo: view.topAnchor).isActive = false
        
        
        /*CONSTRAINTS LABEL*/
        //LeftAnchor
        lblTitle.leftAnchor.constraint(equalTo: view.leftAnchor, constant: UIScreen.main.bounds.width / 3).isActive = false
        //TopAnchor
        lblTitle.topAnchor.constraint(equalTo: view.topAnchor, constant: UIScreen.main.bounds.height / 2).isActive = false
        //BottomAnchor
        lblTitle.bottomAnchor.constraint(equalTo: view.bottomAnchor, constant: 10).isActive = false
        //RigthAnchor
        lblTitle.rightAnchor.constraint(equalTo: view.rightAnchor).isActive = false
        //HeightAnchor
        lblTitle.heightAnchor.constraint(equalToConstant: 100).isActive = true
        //WidthAnchor
        lblTitle.widthAnchor.constraint(equalToConstant: 250).isActive = true
        
        
        /*CONSTRAINTS BOTON*/
        btnClick.rightAnchor.constraint(equalTo: view.rightAnchor).isActive = true
        
        
        /*CONSTRAINTS IMAGEN USER*/
        imgView.leftAnchor.constraint(equalTo: containerView.leftAnchor).isActive = true
        imgView.topAnchor.constraint(equalToConstant: view.topAnchor).isActive = true
        imgView.rightAnchor.constraint(equalTo:view.rightAnchor).isActive = true
        imgView.bottomAnchor.constraint(equalTo: containerView.bottomAnchor).isActive = true
        imgView.heightAnchor.constraint(equalToConstant: 20).isActive = true
        imgView.widthAnchor.constraint(equalToConstant: 20).isActive = true
        
       //Cuando tenemos un stack view que no tiene con
        
        
        
       /* let xConstraint = NSLayoutConstraint(item: lblTitle, attribute: .centerX, relatedBy: .equal, toItem: nil, attribute: .centerX, multiplier: 1, constant: 0)
        
        lblTitle.addConstraint(xConstraint)*/
        
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        
        setupViews()
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}
