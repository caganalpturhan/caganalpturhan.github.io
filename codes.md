[Home](README.md) | [Projects](projects.md) | [Reflections](reflections.md) | [Codes](codes.md)

<li>import SwiftUI

struct ContentView: View {
    @State private var hour = 10
    @State private var minute = 0
    
    var body: some View {
        ZStack {

            if hour < 6 {
                Color.black.ignoresSafeArea()   
            } else if hour < 12 {
                Color.blue.ignoresSafeArea()    
            } else if hour < 18 {
                Color.yellow.ignoresSafeArea()  
            } else {
                Color.orange.ignoresSafeArea() 
            }
            
            VStack {
                
                ZStack {
                    Circle()
                        .frame(width: 250, height: 250)
                        .foregroundColor(.white)
                        .overlay(Circle().stroke(.black, lineWidth: 4))
                    
                   
                    Rectangle()
                        .frame(width: 8, height: 70)
                        .foregroundColor(.black)
                        .offset(y: -35)
                        .rotationEffect(.degrees(Double(hour % 12) * 30))
                    
                  
                    Rectangle()
                        .frame(width: 4, height: 100)
                        .foregroundColor(.red)
                        .offset(y: -50)
                        .rotationEffect(.degrees(Double(minute) * 6))
                    
                    
                    Circle()
                        .frame(width: 20, height: 20)
                        .foregroundColor(.black)
                }
                
           
                Text("Hour: \(hour), Minute: \(minute)")
                    .font(.title)
                    .foregroundColor(.black)
                    .padding()
            }
        }
      
        .onTapGesture {
            minute += 5
            if minute == 60 {
                minute = 0
                hour += 1
                if hour == 24 { hour = 0 }
            }
        }
    }
}

#Preview {
    ContentView()
}

</li>
