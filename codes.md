[Home](README.md) | [Projects](projects.md) | [Reflections](reflections.md) | [Codes](codes.md) | [Videos](videos.md)

<h2>Swift Design Challeng V1</h2>
import SwiftUI

struct ContentView: View {
    let aiTopics = [
        "🤖 Machine Learning",
        "🧠 Neural Networks",
        "📊 Data Analysis",
        "💬 Natural Language Processing",
        "🎨 AI Creativity"
    ]
    
    var body: some View {
        NavigationView {
            VStack(alignment: .leading, spacing: 16) {
                Text("AI")
                    .font(.largeTitle)
                    .fontWeight(.bold)
                
                Text("Key topics in artificial intelligence")
                    .font(.subheadline)
                    .foregroundColor(.gray)
                
                List(aiTopics, id: \.self) { topic in
                    Text(topic)
                        .font(.body)
                }
                .listStyle(InsetGroupedListStyle())
            }
            .padding()
            .navigationBarHidden(true)
        }
    }
}







struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

<h2>List Project Icecream</h2>
import SwiftUI

struct ContentView: View {
    let flavors = ["Vanilla", "Chocolate", "Strawberry"]
    let scoops = [2, 3, 1]
    
    var body: some View {
        VStack {
            Text("🍦 Ice Cream List").font(.title)
            
            ForEach(0..<flavors.count, id: \.self) { i in
                Text("\(flavors[i]) - \(scoops[i]) scoops")
            }
        }
        .padding()
    }
}







